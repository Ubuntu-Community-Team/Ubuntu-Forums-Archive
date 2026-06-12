---
title: "Upgrade 7.04 to 8.04, Can't do *anything*!!"
date: 2008-11-16
forum: General Help
---

### Post by lalawawa on 2008-11-16
I just brought up 8.04 for the first time, and I can't get started.  There's no "system" menu, no "applications" menu.  I don't see how I'm to get to the package manager to download emacs, or how I would run it if I could.  I don't see how I'm supposed to get to a command line.  I can't do anything useful!

An exacerbating issue is that my monitor is 1920x1280, and it's not displaying the rightmost portion of the screen.  I can just see the beginning of the date at the rightmost edge of the top bar.  If I move the mouse off to the right of that, it tells me I can bring up the menu to Log off, etc.

---

### Post by lalawawa on 2008-11-16
I figured out what it is.  The "system" and "application" menus are to the left of the screen where I can't see them.  I don't know how, but somehow I'm going to have to figure out how to navigate them when I can't see what I'm clicking on.  Slick.

---

### Post by lalawawa on 2008-11-16
Well, stumbling in the dark off to the left side of the screen I managed to bring up a terminal, sudo emacs, and edit my /etc/X11/xorg.conf to include 1920x1280 resolution.  Rebooted and now the "Applications" "Places" and "Systems" buttons are visible to the left which is a BIG improvement.  There still is some space off to the right end of the screen that I can't see but it's not as big an impediment as missing the left of the screen was.

I tried going to System->Preferences->Screen Resolution and selecting 1600x1200 but it doesn't help.

---

### Post by CJ Master on 2008-11-16
Many monitors come with buttons that allow you to stretch the image in and move it sideways/vertically. That might help ya.

---

### Post by lalawawa on 2008-11-16
That helped a lot!  I love you!  It now displays 1600x1200 properly.  I had 1920x1280 displaying when I was 7.04, but just having a properly working computer is helpful.  I think I'll finish setting up my computer now and worry about getting the higher res later.

---

