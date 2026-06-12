---
title: "Slave Drive"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by kievking on 2006-03-16
I installed 5.10 and grub on my primary slave, 3rd partition. This is how I set it up: /dev/hdb3 or hd1,2.     I got the following boot error:  error 22 - partition doesn't exist.  Any assistance will be appreciated.

---

### Post by Ocxic on 2006-03-16
can you post your /boot/grub/menu.lst it would help, and how you have your hard drives and partitons setup

---

### Post by taurus on 2006-03-16
If it is a third partition of a second harddrive, then it is known as /dev/hdb3...

---

### Post by kievking on 2006-03-16
[QUOTE=Ocxic]can you post your /boot/grub/menu.lst it would help, and how you have your hard drives and partitons setup[/QUOTE]

Thanks for quick reply

Menu List:

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


I have XP on my primary Master, I have Ubuntu on my External USB drive(turned off during boot up of the primary slave),  

My primary slave is partitioned as follows:

hdb1 - fat32    20GB
hdb2 - ext3     20GB
hdb3 - ext3  ubuntu 5.10 and Grub    30GB
hdb4 - something that ubuntu installation created
hdb5 - swap

---

### Post by kievking on 2006-03-16
Nevermind. Problem solved.  I learned that if grub is installed on the Primary Slave   Drive and it's the first boot option, then Grub detects it as the Primary Master (hd(0,2)) instead of the Primary Slave (hd(1,2)). Thanks for the replies.

---

