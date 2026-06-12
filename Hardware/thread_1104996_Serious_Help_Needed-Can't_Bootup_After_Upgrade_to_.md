---
title: "Serious Help Needed-Can't Bootup After Upgrade to 8.10"
date: 2009-03-24
forum: Hardware
---

### Post by grwilbourn on 2009-03-24
First of all, I'm looking at a laptop for a fellow employee that got it from the Federal Trade Commission settlement in the 'Blue Hippo' issue. It came with linux installed as the OS. It works (worked) fine except when you put a DVD or CD in the drive it gives a msg that it can't find the drive.
2nd, I went to another Linux support site and posted there. They suggested and I did the 'mount' command but the DVD/CD drive still didn't respond. Mount gave me the following msg:

[I][I]root@ubuntu:~#mount
/dev/sdal on /type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuidm,nodev)
varru on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev tyhpe tmpfs (rw,mode=0755)
devshm on/dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
root@ubuntu:~#[/I][/I]

They then suggested to upgrade to either 8.04 or 8.10. I went to System|}Administrtion|Update Manage and ran the Upgrade Option and it installed 8.10. On reboot I get the following msg:

[I]Starting up...
Loading, Please Wait...[indent]Check root = bootarg CAT /proc.Cmdline[indent]or missing modules, devices: CAT/proc/modules 1s /dev

Alert! /dev/disk/by-unid/553cbf15 - ced8 - 4a1w -9092 3a0127a47cce desn not exist. Dropping to a shell!

Busy Box v1.1.2 (Debian 1:1.1.2 - 5ubuntu12) Built-in shell (Ash)
Enter 'help' for a list of built-in commands
(initramfs)[/I]

I posted this and no one has responded back since. I did try to reinstall using a CD but again, the drive isn't working.
I would like to get this laptop back to functional status if anyone can help me. The hardware only has the name of 'Linux Certified' with a Model #  S62E/LC2210S. 

I found this site for the LC2210S: [http://www.linuxcertified.com/linux-notebook-lc2210s.html](http://www.linuxcertified.com/linux-notebook-lc2210s.html)

Any help at all would be greatly appreciated... Thanks....

---

### Post by mlentink on 2009-03-27
Do you have another pc available?
If so, try to create a bootable usb-drive, e.g. per [this]("http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/") or, for windows, [this]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/")

---

### Post by mlentink on 2009-03-27
Do you have another pc available?
If so, try to create a bootable usb-drive, e.g. per [this]("http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/") or, for windows, [this]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/")

and [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by grwilbourn on 2009-03-27
Thanks for you reply and I'll work on that today and get back to you a little later

---

### Post by grwilbourn on 2009-03-30
Okay, I'm lost!!! Here is my situtation, I'm working on a Ubuntu laptop that when I attempted to upgrade to 8.10 it will not boot. I only have available window OS machines to make the bootable flash drive with. I downloaded the two files from your links above and I can't get them to launch in Windows....
Help Please!!!!

---

