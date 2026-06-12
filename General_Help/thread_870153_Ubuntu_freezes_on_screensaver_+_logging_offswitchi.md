---
title: "Ubuntu freezes on screensaver + logging off/switching users"
date: 2008-07-25
forum: General Help
---

### Post by Joe of loath on 2008-07-25
hi;

this computer is being a pain. some idiot called the motherboard 'winfast' for a reason...

anyway, everything seems to work fine on my login, but if anyone else leaves the computer on the screensaver, sometimes the computer will freeze, other times the mouse pointer will move, but the password box will be behind the screensaver. I can ctr-alt-F1 to another virtual terminal, but can't kill the screensaver without completely screwing up gnome.

also, when I go to switch user or log off, a similar thing happens, with the light brown background and nothing else. the mouse cursor still moves. I have tried disabling video drivers, and that isn't the problem.

the only way to fix any of it is to press the button, and wait 2 minutes for the reboot.

can anyone help?
thanks
Joe :mad:

---

### Post by rkeidel on 2008-07-25
Same here. The screen saver comes up, or if I log the work station. After a couple of minutes the systems freezes. I did not tried Ctrl+Alt+F1.

---

### Post by Joe of loath on 2008-07-26
> **rkeidel said:**
> Same here. The screen saver comes up, or if I log the work station. After a couple of minutes the systems freezes. I did not tried Ctrl+Alt+F1.

just out of curiosity, what hardware are you running?

---

### Post by Joe of loath on 2008-07-26
ok, here are some pictures of Dmesg after the crash. sorry I couldn't do text, but it didn't like me piping through nano. (worked fine on debian, not sure what the problem is here).

[IMG]http://i274.photobucket.com/albums/jj269/joeofloath/RIMG0222.jpg[/IMG]

[IMG]http://i274.photobucket.com/albums/jj269/joeofloath/RIMG0220.jpg[/IMG]

[IMG]http://i274.photobucket.com/albums/jj269/joeofloath/RIMG0219.jpg[/IMG]

looks like something wrong with the AGP in the kernel?

---

### Post by Joe of loath on 2008-07-28
narrowed it down. I have a foxconn motherboard don't I?

runs stably with ACPI turned off in the bios, but really slowly. turn it back on, and things start crashing. damn.

---

### Post by rkeidel on 2008-07-28
I have DELL Latitude D531.

---

