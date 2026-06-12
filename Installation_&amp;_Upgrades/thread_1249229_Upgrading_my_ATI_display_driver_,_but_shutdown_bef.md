---
title: "Upgrading my ATI display driver , but shutdown before it finish...."
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by pumber on 2009-08-25
I , by accident, shut down the computer while I am downloading the ATI displayer driver. Afterwards, I could not boot to Ubuntu 9.0.6 64amd. It goes black screen after showing the ubuntu logo for a while.
How to fix it ? Thank you !

---

### Post by Mark Phelps on 2009-08-25
You most probably forced the install of a video driver that's incompatible with your card/chip and Ubuntu 9.04.  What video card/chip are you using?  To find out, boot into a console (Ctrl-Alt-F2) and type "lspci".

---

### Post by SteveONCSU on 2009-08-25
If grub loads, you could press ESC and try loading your latest kernel in recovery mode.  At the bottom of that menu you'll see an option to attempt fixing video problems.  From what I can tell, this just wipes your xorg.conf clean.  Now you can resume normal boot and it will hopefully load the ubuntu interface.  You'll then have to reinstall your video driver.

---

