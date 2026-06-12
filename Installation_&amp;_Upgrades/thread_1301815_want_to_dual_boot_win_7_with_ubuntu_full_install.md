---
title: "want to dual boot win 7 with ubuntu full install"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by kmaster228 on 2009-10-26
ok so i want to dual boot windows 7 with ubuntu karmic, but the thing is my computer has a just karmic, no windows, so when i installed windows on a another partition and booted into a live cd, their was no grub command when it says type sudo grub like the instructions from here: [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999). so now i can only boot into windows, please help

---

### Post by xtjacob on 2009-10-26
I think you have to install the grub packedge from synaptic. If your using an ubuntu 9.10 cd it only has the latest version of grub. I don't know the command for the latest version though. :???:

---

### Post by kmaster228 on 2009-10-27
Thanks for your response, but where would i install grun through, the live cd? and should i use my jaunty cd and try?

---

### Post by kmaster228 on 2009-10-27
BUMP; please help i really want to access my ubuntu, does any one know the commands for grub 2

---

### Post by Earl_Maroon on 2009-10-27
Boot up with your live CD and go to the terminal. Type ```
sudo grub
```
Then enter ```
root (hdA,B)
``` where A is the hard disk number (starting from 0) and B is the partition number of your root partition (so the first disk first partition is "(hd0,0)").
Then```
setup (hdA)
``` where A is the same as above.
Then ```
quit
```
Reboot and you should have the grub menu on boot.



(To check your partitions type in a terminal ```
cat /etc/fstab
```)

---

### Post by oldfred on 2009-10-27
See also:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by BigG123 on 2009-10-27
Better with Windows installed first.  Otherwise you have to add it to the boot loader witch can be tricky in Grub2 as it's difficult to edit.

---

### Post by kmaster228 on 2009-10-27
thanks so much, ill try this

---

