---
title: "Unable to install Ubuntu"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by rian4me on 2009-04-05
I have win xp sp3 on my c drive
I tried installing ubuntu 8.04 on to my d drive by making 
c drive as mount point "/windows"
and d drive as mount point "/" with ext3 format
and a small 2 gb e drive as swap space
the problem is it installs everything properly and then when it asks to restart and i do so
Windows xp just boots up directly to the progress bar screen

no grub loader is shown :(
i did  this many times and it doesn't work 
Help
Please don't direct me to a tutorial for step by step installation procedure, i have already read lots of those

just tell me what could be the possible problem and how to solve it

---

### Post by Meson on 2009-04-05
If your c and d drivers are separate physical disks, you need to tell your bios to boot from the d drive.  If they are just separate partitions, then it doesn't sound like you installed GRUB.

---

### Post by ongun.kanat on 2009-04-05
try reinstall grub to your hard drive as "/dev/sd*" it can be installed on 'D'

---

### Post by Mark Phelps on 2009-04-06
OK -- no tutorials ...

Where'd you install GRUB.  To the MBR? Or to the Ubuntu root partition?

To find out, boot from the LiveCD, open a terminal, and do the following:
1) enter  "grub"
2) enter "find /boot/grub/stage1"

That will indicate where GRUB is installed.

---

