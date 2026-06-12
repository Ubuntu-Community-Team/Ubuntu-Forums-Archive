---
title: "Getting Ubuntu 9.10 to start in gui"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by mrmagoo1077 on 2009-11-08
When I boot up my PC, it says grub loading than the screen goes black and will sit there until I hit Control+alt+delete.  Than it restarts and brings me to the menu where i can select Ubuntu recovery.  if i hit start normal boot, it brings me to the comand prompt.  And if I hit startx i get to the gui.  But this is a real hassle to do everytime i want to boot my computer.  How can i fix it to go to the gui?

---

### Post by MainframeGuy on 2009-11-09
I have a similar problem, but only SINCE I resolved the audio problems with my audigy card.

And this leads me to suspect that it has to do with previous .conf settings that maybe have carried over with the upgrade to the new release.  The problem is not with the gui or gnome at all - it is something that prevents the logon going through smoothly... but what the fix is I have yet to discover.... Anyone else any clues?

---

### Post by mrmagoo1077 on 2009-11-10
well mine is a full intsall, not an upgrade.  And i did not have any audio problems.  But I wonder if the cause is the same.  any ideas?

---

### Post by MainframeGuy on 2009-11-10
I have just discovered that although I can get most functionality when I use STARTX after logon fails the sound is not working (although it did when I first resolved the problem by installing ALSA mixer).  After STARTX the ALSO mixer does not start properly.  I suspect it would run fine from the shell... This leads me to think the configuration for ALSA is not working during logon perhaps more also is breaking things - I shall have to look further when I have time.  ANy useful info here appreciated meanwhile though!

---

