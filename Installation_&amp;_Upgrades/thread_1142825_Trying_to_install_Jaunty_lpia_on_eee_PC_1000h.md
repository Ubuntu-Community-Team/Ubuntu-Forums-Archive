---
title: "Trying to install Jaunty lpia on eee PC 1000h"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Auslegung on 2009-04-29
I'm trying to install Jaunty alternate lpia iso on my eee PC 1000h and it just won't work.  When I begin to install it gives me the familiar "No common CD-ROM drive was detected."  After a lot of googling and searching ubuntuforums, I've managed to discover that the bug is fixed.  However, I'm stilling having the problem, even with a freshly downloaded .iso.  What is going on?  Can anyone help, or maybe delete all the threads saying the bug is "fixed?"

---

### Post by DarwinSurvivor on 2009-06-04
I am having the same problem.

I am trying to use a eee as an ubuntu server.

I downloaded the 32-bit ubuntu server installer and used the usb-creator tool (built into ubuntu) to tansfer the image to a usb drive.

The problem is, it keeps asking for a cd-rom. The problem is, the machine has no cd-rom.

I have successfully installed ubuntu on a eee before using the same method, but with the graphical installer (live-cd). Is it something specific about the text-based one?

I tried droping to a shell and running:
mount /dev/sdb1 /cdrom

but then when I continue the install, I get "Failed to copy file from CD-ROM. Retry?"


If anyone has any ideas, It would be greatly appreciated

---

### Post by Brandon Williams on 2009-06-04
[This thread](http://ubuntuforums.org/showthread.php?t=1130866), although not specifically related to the eee, indicates that there is a problem putting an ISO on a USB thumb drive that requires the Jaunty version of usb-creator. It doesn't specifically say what the problem is, though, so I don't know if he's referring to the issue you're experiencing with the eee. Nevetheless, it may be worth a look.

---

### Post by DarwinSurvivor on 2009-06-04
Well, I never got the server edition to install, but if you remove "persistent" from the boot options, you can install the desktop version just fine.

-Boot from usb
-Select Language
-Hit F6
-use left-arrow key, then backspace to remove "persistent" from the line at the bottom

---

