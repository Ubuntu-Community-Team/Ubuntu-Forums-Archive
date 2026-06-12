---
title: "Triple Boot Impossible"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Tharakanuwanpro on 2009-06-17
Hi ,

Please Help me .

My first OS was windows XP at about an year ago then about 4 months ago i installed vista and it works fine , but now i want to install ubuntu , I installed ubuntu but the bootloader or grub doesn't come , it straight away comes to the Windows Vista Screen .
I have 2 hard disks , one 76 GB and the other was divided into 4 partitions but now after installation it became 6 partitions all and i have Xp , Vista and Ubuntu on the same Hard Disk . I installed with the manual method (setting up the swap and used 2 ext4 partitions , one with  "/" and the other with "/home" .

Please Help me

---

### Post by sedawk on 2009-06-17
Can you boot from a LiveCD and post the output of
```

sudo fdisk -l

```
This gives a clearer picture of your disk layout.

How do you boot XP if your computer directly starts with Vista?
Do you get the Vista boot manager (or whatever it is called).
You can install grub to boot XP, Vista and Ubuntu, but if you
have a Vista boot manager you can also try to add Ubuntu to
that Boot Manager instead ...

---

### Post by Tharakanuwanpro on 2009-06-19
How can i add Ubuntu to Vista Boot Manager please tell me that

---

### Post by dstew on 2009-06-19
The easiest way is to use EasyBCD. This Windows program manipulates the Windows boot system using a graphical interface, and helps you setup multiple boot scenarios. You will need to install neogrub into the boot sector of your Linux partition. See [this How-To]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5").

---

