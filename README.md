# Tab Related Confirmation Library for Firefox 3.5-56

This project is obsolete and not maintained anymore.

## Usage:

    Components.utils.import('resource://my-modules/confirmWithTab.js');
    
    var checkbox = {
          label   : 'Never ask me',
          checked : false
        };
    
    confirmWithTab({
      tab      : gBrowser.selectedTab,           // the related tab
      label    : 'Ara you ready?',               // the message
      value    : 'treestyletab-undo-close-tree', // the internal key (optional)
      buttons  : ['Yes', 'No'],                  // button labels
      checkbox : checkbox,                       // checkbox definition (optional)
      cancelEvents : ['SSTabRestoring']          // events to cancel this deferred (optional)
    })
    .next(function(aButtonIndex) {
      // the next callback receives the index of the clicked button.
      switch (aButtonIndex) {
        case 0: // Yes
          ...
          break;
        case 1: // No
          ...
          break;
      }
      // after the notification bar is closed, "checked" indicates
      // the state of the checkbox when the user clicks a button.
      var checked = checkbox.checked;
      ...
    })
    .error(function(aError) {
      // if the tab is closed, or any event in the cancelEvents array
      // is fired, then an exception is raised.
      ...
    });

