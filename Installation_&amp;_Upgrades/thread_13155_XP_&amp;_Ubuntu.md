---
title: "XP &amp; Ubuntu?"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by Benny on 2005-01-29
Hi!
I've installed XP and Ubuntu. When i boot my pc and try to boot in XP i get this message.

Booting 'Windows NT/2000/XP'

root (hd0,0)
  Filesystem type unknown, partition type 0x7
savedefault 
makeactive
chainloader +1

..After this my pc stop. It wont boot to XP.

Ubuntu is booting and working fine.

Can someone help??

---

### Post by rudi on 2005-01-29
is that all you see?! ....
 Is windows XP the first partition on your disk? Try to run cfdisk, there you will see your partition lay-out. Your hda1 should be NTFS (windows). If another partition is formatted as ntfs try to change your /boot/grub/menu.lst entry of Windows XP (e.g. hd(0,1) for hdab.

---

### Post by Benny on 2005-01-29
Okay, i tryed cfdisk, but i get this..

FATAL ERROR: Bad logical partition 7: enlarged logical partitions overlap

I dont know what to do?!
Should i install XP & Ubuntu  again or is there some real noob instruction to correct this without reinstalling?

And when i try to go /boot/grub/menu.lst system says "Permission denied"?
I'm logged as a root.

---

### Post by rudi on 2005-01-29
humz, how precisely have you partitioned your drive? Did you used the Ubuntu installers partition tool, partition magic, Microsoft's fdisk. Some more information would be usefull. Post your partition lay-out if possible. 
 
 The error you've described sounds like a faulty partition table. I never have encountered it myself, but my initial reaction would be, back up your files, erase the whole lot and start over, clean this time. But i'm not familiar with errors due to a defective partition lay-out.
 
 As with the "permission denied error" try this:
 **sudo less /boot/grub/menu.lst**

---

### Post by Benny on 2005-01-29
Thanks Rudi!

It's working finally.

---

