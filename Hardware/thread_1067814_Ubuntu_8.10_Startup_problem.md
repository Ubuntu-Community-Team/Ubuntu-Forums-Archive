---
title: "Ubuntu 8.10 Startup problem"
date: 2009-02-12
forum: Hardware
---

### Post by ventru on 2009-02-12
Hi.
I've got a problem with launching Ubuntu 8.10 on my laptop Acer Aspire 5051AWXMi. When I'm starting up the system I have this message (then I must type in „exit” to get into GUI):

Boot from (hd0,0) ext3	9b5b1f24-3edd-4a7b-9e88-86225397046d
Starting up...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
Check rootdelay= (did the system wait long enough?)
Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/e5bbb727-26c8-4a0a-a1d7-570bf0099f51 does not exist.
Dropping into a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

Can someone help me with this?
Thanks.

---

### Post by mikewhatever on 2009-02-12
Can you post the outputs of the following commands:
cat /etc/fstab
cat /boot/grub/menu.lst | grep UUID
sudo blkid

---

### Post by ventru on 2009-02-14
That's what I get:

cat /etc/fstab:

# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda5 
UUID=e5bbb727-26c8-4a0a-a1d7-570bf0099f51 /               ext3    relatime,errors=remount-ro 0       1 
# /dev/sda1 
UUID=9b5b1f24-3edd-4a7b-9e88-86225397046d /boot           ext3    relatime        0       2 
# /dev/sda6 
UUID=0d471fef-d426-46ae-805b-82bb7bcb7c8b none            swap    sw              0       0 

cat /boot/grub/menu.lst | grep UUID:

cat: /bot/grub/menu.lst: No such file or directory

sudo blkid:

/dev/sda1: UUID="9b5b1f24-3edd-4a7b-9e88-86225397046d" TYPE="ext3" 
/dev/sda5: UUID="e5bbb727-26c8-4a0a-a1d7-570bf0099f51" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="0d471fef-d426-46ae-805b-82bb7bcb7c8b" 
/dev/sdb1: LABEL="USB Drive" UUID="D439-4564" TYPE="vfat" 
/dev/loop1: UUID="c6550b60-0178-41c6-943a-b32fc135c3f0" TYPE="ext3"

---

### Post by saunders on 2009-02-14
I'm having this problem too, but only when I try to boot using the latest -rt kernel (2.6.27.3-rt I think). The generic kernel boots fine. I'm using a Dell Inspiron 1300, Ubuntu 8.10 single boot.

A quick google suggested I try adding rootdelay=90 to the -rt kernel entry in grub.lst, which didn't work. Neither did adding all_generic_ide to the same line in grub.lst. One last suggestion was to replace the UUID number with /dev/sda1 (my boot partition). This didn't work either.

It's a pain...I've used the -rt kernel successfully before on Gutsy and Hardy. I replaced the hard drive in my laptop before installing Intrepid. I'm guessing something about the combination of HD and -rt kernel is causing the problem, but I don't know how to fix it!

---

