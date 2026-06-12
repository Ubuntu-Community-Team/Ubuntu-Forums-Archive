---
title: "Aut-mounting external HDDs by UUID?"
date: 2008-06-06
forum: Hardware
---

### Post by clk99 on 2008-06-06
I am running Kubuntu 8.04 and I have two external hard drives that I use on a regular basis.  I would like them to automatically mount when I start my computer, but am having some trouble getting this to work.  I can't use their device names (sdb1, sdc1) because they interchange occasionally, along with other peripherals like my ipod, so I set up my fstab using the UUIDs of my drives, like so:
```
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=8e1146c8-0eee-4b30-b08f-7dcad44b8652 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=54ad4be3-c607-4e3a-9dbd-87899edf333b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
UUID=8AB0D69BB0D68D57 /media/external ntfs-3g defaults,force,locale=en_US.utf8 0 1
UUID=F078AEBD78AE81C8 /media/external2 ntfs-3g defaults,force,locale=en_US.utf8 0 1
```This should work, right? Well, it doesn't.  When I boot up the drives are recognized, but unmounted.  If I try to open one, for instance external2, I am taken to system:/media/sdc1 with a 'Permission denied.' error.  The only way I can get the drives to mount after booting up is to open up the terminal and manually mount them by UUID with:
```
sudo mount UUID=8AB0D69BB0D68D57
sudo mount UUID=F078AEBD78AE81C8
```Anyone have any idea what my problem is or how I can fix it?

---

### Post by clk99 on 2008-06-11
I've now found out that sometimes the drives will automatically be mounted after booting up, but usually not.  Anyone?

---

