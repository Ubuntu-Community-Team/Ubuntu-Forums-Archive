---
title: "mouse briefly hangs when typing"
date: 2010-02-01
forum: Hardware
---

### Post by toolunious on 2010-02-01
Hi,

It is impossible to move the mouse briefly when I type any letter or use any character in combination with a function key. I tried looking at the gconf-editor and tried making some changes in the keyboard/mouse settings, none of which seem to help.

It's quite bothersome when using text editors!

Where should I look at to debug this? Google didn't help I'm afraid.

---

### Post by Rhubarb on 2010-02-01
I presume you're on a laptop there.
If so, it's an easy fix:-

System --> Preferences --> Mouse
Select the "Touchpad" tab
Uncheck the box marked "Disable touchpad while typing"

---

### Post by toolunious on 2010-02-02
Sorry for not pointing out that I am on a desktop pc. I have tried the fix though, it didn't work. I'm going to try another keyboard/mouse, maybe that works. Any help is still wished for. I haven't used the mouse preferences "touchpad" of course, I used {[gconf-editor] >> Desktop > Gnome > Peripherals > Mouse}.

---

### Post by Rhubarb on 2010-02-02
I ran into a similar problem to this a few years back when I was getting wiimotes working in Ubuntu.

Could you check to see if the **mouseemu** package is installed on your system?
If it is, and you don't need it, remove that package and everything should work nicely again.
Alternatively, if you need mouseemu to be installed, then follow [this]("http://ubuntuforums.org/showthread.php?t=402296") thread and change mouseemu's configuration file to suit.

---

### Post by toolunious on 2010-02-04
Excellent! I wasn't going to use the WII remote any time soon anyway :) thanks!

---

