---
title: "GRUB read error"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by 3do on 2009-09-22
I've just installed Ubuntu on a 80Gb ide drive for the first time but after the install it gave me a GRUB read error.

How can i fix this error as i don't know what to do?

Cheers for any help i get.

---

### Post by dstew on 2009-09-22
What is the error number? Does it happen before you see the grub menu, or after?

---

### Post by 3do on 2009-09-23
The error is a stage 1.5 error but i get no error number.

*Edit* i'm now getting an error 18

---

### Post by tommcd on 2009-09-23
As a (hopefully) easy fix, try reinstalling grub to the MBR from the live CD like this:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

---

### Post by 3do on 2009-09-23
I am now getting an error 16 after re-installing grub.

---

### Post by tommcd on 2009-09-23
See this about grub error 16:
[http://members.iinet.net.au/~herman546/p15.html#16](http://members.iinet.net.au/~herman546/p15.html#16)
TRy booting from the Ubuntu live CD, open a terminal, and run fsck to check the file system:
```
sudo fsck -f /dev/sdXY
```
Replace XY with the drive and partition numbers for your Ubuntu root partition. For example, for me it would be:
```
sudo fsck -f /dev/sda2
```
It looks like something is screwed up somewhere. I'm wondering if this is more than just a grub configuration problem. Anyway, try fsck from the live CD and reboot.
Also, can you post your /boot/grub/menu.lst file.

---

### Post by presence1960 on 2009-09-23
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

