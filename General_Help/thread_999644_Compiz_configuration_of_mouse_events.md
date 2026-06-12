---
title: "Compiz configuration of mouse events"
date: 2008-12-02
forum: General Help
---

### Post by nicholas.alipaz on 2008-12-02
This is something that has been bothering me.  In compiz, under Desktop Wall, Bindings.  There is the option to bind mouse events to "move within wall" but not "move with window within wall"

Is there somewhere that a bug could be posted about this, or perhaps a workaround?

---

### Post by nicholas.alipaz on 2008-12-02
I was able to put together an alternative from a bunch of threads on fixing mouse issues with keybindings.

Install xautomation and xbindkeys.  Add the following to one's xbindkeysrc file.  
```
# Change tilt wheel right to do Ctrl+Alt+Shift+Down
"/usr/bin/xte 'keydown Alt_L' 'keydown Control_L' 'keydown Shift_L' 'key Down' 'keyup Shift_L' 'keyup Control_L' 'keyup Alt_L' &"
m:0x0 + b:7 

# Change tilt wheel left to do Ctrl+Alt+Shift+Up
"/usr/bin/xte 'keydown Alt_L' 'keydown Control_L' 'keydown Shift_L' 'key Up' 'keyup Shift_L' 'keyup Control_L' 'keyup Alt_L' &"
m:0x0 + b:6
```
Then go to System -> Preferences -> Sessions and add a new startup program.  use 'xbindkeys' (without quotes) for the command.

However, it still would be nice if this were configurable from the compiz configuration.  The compiz key/mouse bindings seem to work well.

---

