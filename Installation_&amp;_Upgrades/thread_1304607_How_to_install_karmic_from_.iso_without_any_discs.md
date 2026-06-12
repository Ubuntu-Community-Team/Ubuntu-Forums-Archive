---
title: "How to install karmic from .iso without any discs"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by dj-toonz on 2009-10-29
Hi all, Just downloaded Karmic 9.10 (tock 10 minutes to download) but just found out I've got no CD's to burn to :( but I've got a 2GIG flash drive. is there any program I can use to put the ISO file onto the Flash Drive & boot the System from that, The desktop Supports Booting from USB

---

### Post by sisco311 on 2009-10-29
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by Cigaras on 2009-10-29
[[IMG]http://sourceforge.net/dbimage.php?id=167328[/IMG]]("http://unetbootin.sourceforge.net/")

---

### Post by MountainX on 2009-10-29
I want a solution that doesn't require a USB stick or Windows. I want to do it from a HDD on a computer already running Linux.

There is an old post on how to do this with Fiesty here:
[http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)

I want to copy the Karmic ISO to my hard disk on the computer where it will be installed. 
I think I could make a partition and copy vmlinuz and initrd.xxx and the ISO file there.
Then I could manually edit /boot/grub/menu.lst as required.
But so far I have not found the exact steps. (For example, is fromiso=/path/filename.iso required in menu.lst?)

---

### Post by sisco311 on 2009-10-29
> **MountainX said:**
> I want a solution that doesn't require a USB stick or Windows. I want to do it from a HDD on a computer already running Linux.

There is an old post on how to do this with Fiesty here:
[http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)

I want to copy the Karmic ISO to my hard disk on the computer where it will be installed. 
I think I could make a partition and copy vmlinuz and initrd.xxx and the ISO file there.
Then I could manually edit /boot/grub/menu.lst as required.
But so far I have not found the exact steps. (For example, is fromiso=/path/filename.iso required in menu.lst?)

If you want to use the Live CD iso, then you have to create a new ~750MB  partition. (you can use your swap partition)

If you use the Alternate CD, you can use an existing partition. (the root or home partition of your current linux distro)

[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

---

### Post by MountainX on 2009-10-29
> **sisco311 said:**
> 
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Thank you. That's a great link. :)

---

