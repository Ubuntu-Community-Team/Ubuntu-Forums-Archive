---
title: "[SOLVED] Dell latitude D531: CTL-ALT-Fn and external lcd projecto"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by johnwren on 2008-01-16
I have a dell latitude D531 with 2GB memory running under gutsy 7.10.  I'm doing a fresh re-install to track down a few remaining issues: I cannot get an external lcd projector to work off the vga port for my presentation, and (possibly related) the combination CTL-ALT-F1, F2 etc. does not bring up a terminal login screen.

Has anyone been able to use the D531 and an external lcd projector for a presentation?  Here is what I know: 

Running from the live cd, and without doing an installation, the Fn-F8 (crt-lcd function on the dell laptop) acts as a simple toggle between the laptop screen and the lcd projector.  You can't get both working together, but at least each individually work as expected.  Similarly, CTL-ALT-F1 brings up a terminal login screen (as expected) and CTL-ALT-F7 returns you to the Gnome/xorg screen.  Looks like a good start.

Once you load the system, but without any updates and/or restricted drivers, ie at the first boot after the install, CTL-ATL-F1 freezes the system.

With the system installed and fully updated, but without any restricted drivers or any changes at all to anything -- CTL-ALT-F1 usually appears to have no effect at all( but sometimes freezes the system), and Fn-F8 toggles between the laptop screen and 'nothing'.  The lcd projector flickers, says 'adjusting apa' then cancel (it is a SONY SVGA VPL-CS5 - works fine under VISTA on the same laptop)

With the fglx restricted driver installed, CTL-ALT-F1 seems to do nothing, and Fn-F8 toggles between the laptop screen and 'nothing'.  Doing at CTL-ALT-backspace to restart the x terminal causes both the laptop and lcd to display 'nothing', Fn-F8 appears to do nothing and the keyboard is unresponsive.  However ctl-alt-del did reboot the system.  Bringing the system up with the lcd plugged in and running behaves the same way -- the lcd and laptop are both blank, keyboard unresonsive, CTL-ALT-DEL does reboot the system.

I would appreciate any and all comments and help.  I would especially like to hear from any Dell laptop owners who might have got an external lcd projector working.  I am doing a presentation at an international conference next week, and would love to do it under ubuntu.

Thanks

---

### Post by johnwren on 2008-01-16
Replying to my own post.  A suggestion by forlong (in the desktops cusomization forum) had me adjust the bootstring using setupmanager.  This put vga=791 into the grub bootstring, and restored the ubuntu 'splash screen' with the horizontal bar graph of the progress during the initial system load.  It's nice to see something on the screen while you wait for gnome/xorg to bring up the username/login screen!

However, the other problems are as they were.

I'll start another post asking for help on the system-administration-screens and graphics preferences later tonight -- but if anyone knows of some documentation in this area, please point me to it.
Thanks

---

### Post by johnwren on 2008-01-16
replying again to my own post.  I'm trying to understand xrandr.  Is this the answer?

---

### Post by johnwren on 2008-01-17
At the suggestion of konungursvia, I tried the S-video cable as a way of connecting to the external lcd projector.  It works!  So, I have a partial solution to my problem.  I still would like to know the the 'regular vga' cable doesn't work.

---

### Post by rosegarden78 on 2008-01-19
You may consider telling us whether you were able to get it running with Mac/Win.  Just use a dual-boot Mac/Win + Ubuntu system.  No need to choose favorite.  Just use Ubuntu software to make presentation.  Then use Mac/Win to present it.  Let us know!

I have posted my a similar solution here:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by johnwren on 2008-01-19
Rosegarden, thank you for your suggestion.  I will do some research on this.  In the meantime, it appears I have an unexpected partial solution involving frame buffer handling.  I'm not sure about this, but see the posting on: [http://ubuntuforums.org/showthread.php?t=667271](http://ubuntuforums.org/showthread.php?t=667271)

I can now connect an external lcd screen to the vga port and use it (providing it is turned on when the system reboots.  

Thanks again to everyone in the forum who has helped.

---

### Post by johnwren on 2008-01-22
The CTL-ALT-Fn problem is solved.  See thread [http://ubuntuforums.org/showthread.php?t=667271](http://ubuntuforums.org/showthread.php?t=667271)
I'll mark this thread as solved also, although I am still working on the external lcd problem.

---

