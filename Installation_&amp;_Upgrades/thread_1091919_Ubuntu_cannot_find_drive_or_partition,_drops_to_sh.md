---
title: "Ubuntu cannot find drive or partition, drops to shell"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by kulpojke on 2009-03-09
I am trying to install Ubuntu 8.10 AMD64 on my desktop computer.
The computer has a pentium core 2 duo processor and MSI P4M900M2 motheboard.

I previously had windows XP 64bit :( running on it, but decided to get rid of that and install Ubunutu, because I like it better.  However, after installation, when I reboot it gives the following complaint:

> Gave up waiting for root device. Common problems:
> - Boot args (cat/proc/cmdline)
>   -Check rootdelay= (did the system wait long enough?)
>   -Check root= (did the system wait for the right device?)
> - Missing modules (cat /proc/modules; ls /dev)
> ALERT! /dev/disk/by-uuid/e53cd9ac-c419-4c19-9b11-c68c68c9d2b does not exist. Dropping to shell! 

From other forum posts I gather that GRUB is looking for a drive, probably the drive with the boot point on it (or maybe its looking for / ?) and can't find it because it is looking for the wrong uuid.  Is this something like what is really going on, or am I way off?  Regardless, how can I fix it? 

I have installed it several times now, using the guided partition, and manual partition, but it never works.  I have also run the disk check and cd check on from the live cd. Also, I did the md5sum on the live cd and it was correct. 

This is driving me crazy

---

### Post by miklcct on 2009-04-08
change /boot/grub/menu.lst to not using uuid but instead the actual device file.

---

### Post by dantakeoff on 2011-12-23
How do i do that? please tell me...i have exactly the same problem...:(

---

### Post by nothingspecial on 2011-12-23
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

