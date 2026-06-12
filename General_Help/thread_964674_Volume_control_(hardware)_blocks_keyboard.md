---
title: "Volume control (hardware) blocks keyboard"
date: 2008-10-31
forum: General Help
---

### Post by ztrange on 2008-10-31
Hi all

Just upgraded from hardy to intrepid and almost everything seems to be working fine. I only have a little isue with the volume control of my laptop...

When i move the digital volume control (is some kind of scroll in the side of the laptop), the volume transparent big icon appears on screen and sets the volume all the way up or down (depending on the direction I moved the control). And the big semi-transparent volume icon stays on screen.

Then, the keyboard becomes blocked and if i press esc, the transparent icon disappears and i can open some programs (i could not open anyting before pressing esc), then, if I open a preogram, i.e. tomboy, i cannot imput anything with the keyboard. The only thing i can do is press ctrl+alt+f2 and make a shutdown -h now

Well, any help would be appreciated, even if it is only in order to disable the hardware volume control.

Thanks in advance.

---

### Post by doctorgreg on 2008-10-31
I am having the same problem on my laptop too.  This has to be some sort of bug for sure. HP ZV6000 AMD 64 2.2Ghz, 1gb ram.

---

### Post by ztrange on 2008-10-31
Please confirm that you have the same problem.

[https://bugs.launchpad.net/fedora/+source/linux/+bug/271706](https://bugs.launchpad.net/fedora/+source/linux/+bug/271706)

---

### Post by doctorgreg on 2008-10-31
yes it is the same problem.  I hit volume up once and it goes to the max. Same with turning it down.  The keyboard gets disabled and also cannot right click for a menu on the desktop.  The volume OSD also stays on.

---

### Post by ztrange on 2008-10-31
Well, it seems to be a bug of de evdev driver in Intrepid so all we can do is wait until is fixed. By the way, a workaround is to press ctrl + alt + f1 to go to text mode and then alt + f7 back to gui; that will stop the infinite loop of the volume control but will not prevent it from happening again.

By the way, yopu may want to reply in the bug report page that you have the same bug in order to let developers know how much people is being affected by it.

---

### Post by ktemkin on 2008-11-09
Here's a tentative 'patch': [http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)

---

