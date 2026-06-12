---
title: "intous wacom working but configuring help needed"
date: 2008-10-25
forum: General Help
---

### Post by sl0throp on 2008-10-25
My wacom intous is working, I have edited the xorg.conf file as is in all the guides that I have read but it is only working as if it is in full tablet mode rather than mouse mode...and it has been driving me crazy.

Can anybody tell me where or how I can adjust some of the wacom settings like, modes, and button assignments all I can seem to find is how to set the pressure sensitivity.

tia

s

---

### Post by spupy on 2008-10-25
I use the command line program **xsetwacom**. I think there was some kind of a gui front-end, but I can't remember it.
I couldn't find the docs for xsetwacom in 5 minutes (have to go now), but here is a script that sets some variables when I plug my Wacom Bamboo. You can get some ideas from it I hope.

```
#!/bin/bash

#set mode to "absolute"
xsetwacom set stylus mode absolute

#set scrolling with ring
xsetwacom set pad RelWUp "key core pgdn" 
xsetwacom set pad RelWDn "key core pgup"

#set zoom with ring
# xsetwacom set pad AbsWUp "core key -" 
# xsetwacom set pad AbsWDn "core key +"

# Button <  set to + (Zoom in)
xsetwacom set pad Button1 "core key +"
# Button FN1  set to - (Zoom out)
xsetwacom set pad Button2 "core key -"
# Button > to Ctrl Z (undo)
xsetwacom set pad Button3 "core key ctrl y"
# Button FN2 to Ctrl Y (redo)
xsetwacom set pad Button4 "core key ctrl z"

#setting the buttons on the stylus
# xsetwacom set stylus Button3 3
# xsetwacom set stylus Button2 2
```

---

