---
title: "Boot problem"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by jaxon60 on 2009-10-30
Last night I tried installing 9.10 on a Dell Lattitude D600 notebook. Everything seemed normal (although there was never a notification that installation was complete???) eventually leaving me at a desktop. I shut down and rebooted and it reported no bootable devices found. The computer was running Win XP just prior. A reinstall shows 9.10 installed on the disk. How can fix this?

BTW: Total Linux noob here....

---

### Post by hal10000 on 2009-10-30
I guess the installation did not finish and grub (the boot manager) was not installed correctly.
You can install and setup grub manually, but first we have to verify the current state of your installation. We have to do this step-by-step.

Boot from your live-cd, then open a terminal window and post the output of this command:
```
sudo fdisk -l
```
You can mark the output with your mouse and paste it with the middle mouse button.

---

### Post by axel_2078 on 2009-10-30
I have a similar problem and below is my output:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18705   150247881   83  Linux
/dev/sda2           18706       19457     6040440    5  Extended
/dev/sda5           18706       19457     6040408+  82  Linux swap / Solaris

---

### Post by jaxon60 on 2009-10-31
Well, I ran Darik's Boot and Nuke on the HD, reinstalled succesfully and now boots normally. But seems to have issues...:(

---

