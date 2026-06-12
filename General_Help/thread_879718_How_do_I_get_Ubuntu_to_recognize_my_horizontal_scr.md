---
title: "How do I get Ubuntu to recognize my horizontal scrolling?"
date: 2008-08-04
forum: General Help
---

### Post by nathanscottdaniels on 2008-08-04
I have a Microsoft Wireless IntelliMouse Explorer 2 and Ubuntu 8.04.  The mouse has a total of 9 buttons (left-click, middle-click, right-click, scroll up, scroll down, scroll left, scroll right, and two thumb buttons)  Using some guides online and imwheel as well as hours of labor, I managed to set the two thumb buttons to the features I had them doing in XP (show desktop and go to the next track when listening to music.)

However, my mouse still lacks functionality that I like.  I cannot scroll left or right in applications.  when I run the xev command and try scrolling left or right, nothing is registered where as if I use any other mouse button, something is registered.  This tells me that Ubuntu doesn't even know those buttons exist.  While fiddling with the xorg file I accidentally made my vertical scroll turn into horizontal scroll so I know it is possible.  Now I am stumped.  Can someone help me out?

---

### Post by CatKiller on 2008-08-04
I've never tried this before (not having one of those mice), and I'm not entirely sure which buttons would be the appropriate ones for the horizontal scroll, but would having something like this in your /etc/X11/xorg.conf help?

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "WAxisMapping"          "8 9"
        Option          "Emulate3Buttons"       "False"
        Option          "Buttons"               "9"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection
```

---

### Post by sk0tto on 2008-08-04
There is a program out there called [btnx]("http://www.ollisalonen.com/btnx/").  You will need to download the source code and compile it yourself.

I ran into the same problem with a 9 button dell mouse.  After building the app and running the config for it, I was able to get all of the buttons working just how I wanted.

---

### Post by nathanscottdaniels on 2008-08-04
How do I compile something?  What language is it in?

---

