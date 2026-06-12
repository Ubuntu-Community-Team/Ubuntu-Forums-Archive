---
title: "Installing Grub from LiveCD after some MBR problems.. help"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by tsondie21 on 2009-01-04
Hello.

I decided to install ubuntu on an external hard drive because I do not have much room on my internal laptop hard drive.  After installing it to its own partition on the external, I found that I installed grub onto the internal hard drive. I was able to boot into both ubuntu and vista when the external HD was plugged in, but I was unable to boot into vista when the external was not plugged in.  I repaired the vista MBR and so now I can boot into vista no problem. The only thing, is that I cannot boot into ubuntu now because I erased grub.  Is there any way I can install grub onto the external partition with a LiveCD or is reinstalling my only option.

If reinstalling is my only option, at what point do I choose which HD or partition to install grub into??

Thank you all so much in advance!

---

### Post by Herman on 2009-01-04
There's no need to re-install, all you need to do is boot your Live CD and open a GRUB shell and re-install GRUB to the MBR in the USB drive.
Probably something like:
```
sudo grub
```
```
find /boot/grub/stage1
```
(you use the answer you get from the above command for the input in the next command)
```
root (hd1,0)
```
Where: the results of the second command indicate that (hd1,0) is the correct disk and partition where /boot/grub/stage1 was found.
```
setup (hd1,0)
```
```
setup (hd1)
```
```
quit
```
Then, next time you boot you should be able to press a key such as your F12 key or some other key during boot-up for a list of bootable devices, and choose your USB disk.
If you can't do that, you'll need either a GRUB floppy disk or a GRUB CD to boot your USB with. 
You can use [Super Grub Disk]("http://www.supergrubdisk.org/"), or you can make your own, [How to make your own personalized GRUB Floppy Disk]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make"). -  [How to make your own personalized GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD"). 
Or, you can make a [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"). in your hard disk, if you do that then you won't need to mess around with other media every time you want to boot Ubuntu.

---

### Post by tsondie21 on 2009-01-05
Thank you so much!

---

### Post by Herman on 2009-01-05
Happy Ubuntuing :D

---

