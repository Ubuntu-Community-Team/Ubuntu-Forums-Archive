---
title: "Flashing window contents for certain applications"
date: 2014-02-04
forum: Hardware
---

### Post by darenw2 on 2014-02-04
Almost everything works fine on my Ubunut 12.04 machine, except Blender and Chromium and maybe some others.  With Blender, the contents of the window flash briefly into view then blank out, showing only the background.  The contents flash into view every time I drag the mouse or roll over buttons, but not just moving the cursor over non-control space.   The problem has a good chance of going away when I close Chromium or Firefox pages that use Flash.   Chromium itself also acts messed up, but not the same way as Blender.  It's just weird blinky stuff which looks as if different parts of software fighting for space on the screen to show different things, including the Flash display area.  

This problem has been going on for a while, months, and continued after the last major upgrade to 12.04, and separate upgrades to just Blender or Firefox.  There were some settings in Blender to choose between types of double-buffering and so on, someone recommended changing, but this had no effect.   Other graphics programs - Inkscape, GIMP, and several 3D CAD tools - all work okay.

I suspect this is a problem with the graphics board or its driver, but don't really know.  It doesn't seem to be a problem with Blender itself, buy maybe Blender connects with or uses X Windows or OpenGL in some odd way compared to most other apps.  I have no notion at all why Chromium is flaky. I just don't use it at all any more except rare occasions, mostly to see if it's still buggy.

This machine has a ATI Radeon HD 5450 from Feb. 2011.  The Catalyst Control Center has settings to play with but nothing affects the problem.  I've asked on other forums, been too busy with other things to really follow up, but gotta nail this bug soon so I can use Blender.  The desktop is XFCE4.  I have two monitors each 1920x1080.  16GB main memory.  Apparently 1GB of DDR3 RAM for the graphics.

This information may be too vague to solve the problem. If so, what can I do to produce better diagnostic information?

---

