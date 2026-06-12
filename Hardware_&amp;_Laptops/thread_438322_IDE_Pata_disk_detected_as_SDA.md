---
title: "IDE Pata disk detected as SDA"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by ezacon on 2007-05-09
I have Dell gx270 SFF with a 80Gb IDE (pata) disk with Feisty server. The disk is detected as SDA. I whant to replace it with a 300Gb IDE hard disk. I have cloned the disk with ghost. To rebuid the MBR i have to boot with unbuntu live cd, mount the disk, chroot to mount point and grub-install.
The problem is that when i boot from live ubuntu, the new disk is recognized as hda and grub-install complain sda1 is not found.
What can i do to boot from the new disk?

---

### Post by Rhadamanthos on 2007-05-09
Are you booting from a Feisty liveCD? I know that the changeover from hdX to sdX happened under feisty for a lot of HDs - the ones on my Promise card are no longer detected as hda, etc.

---

### Post by ezacon on 2007-05-10
No. I am using a 6.06 cd. The server was updated from 6.06 to 6.10 and then  to Feisty.
I will download the Feisty cd today and try again. Thanks.

---

### Post by ezacon on 2007-05-10
Confirmed. Same disk is seen as hda with 6.10 and sda with 7.04.
btw. the file /boot/grub/device.map still points to hda and need to be changed to sda to succesfuly do a grub-install

---

### Post by Rhadamanthos on 2007-05-11
Sorry, but I'm a bit new at this. Were you able to successfully edit your map file and get this working?

---

