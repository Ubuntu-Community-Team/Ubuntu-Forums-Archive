---
title: "Hardware config"
date: 2013-09-30
forum: Hardware
---

### Post by coskibum on 2013-09-30
I need some help with a hardware config. I have a new box that I'm putting together and need some help configuring three drives in it. First one is a SSD which I want to hold the the OS and major programs I used which I have done all ready.
Second I need to install a 2 TB drive as a date drive. Third I want to install a 3TB drive as a back up to the data drive.

My question is how to mount the two HHD drives and make sure the data path only goes to the 2TB drive. I don't want to get into a raid config. I want to just use Deja Dup as the back up to the 3TB.

System:
13.04
Asus Sabertooth 990R2.0
AMD 8350 CPU
HIS Radeon 6670
Samsung 840 evo SSD
Toshiba 2tb HHD
Toshiba 3tb HHD

Thanks in advance for any help!

---

### Post by peertje on 2013-09-30
Hi,

Ubuntu won't write anything to any of the mounted hard drives unless you tell it to.

First you're going to have to partition the drives. You can do this easily using gparted, availlable from the store. If you're only using Ubuntu on your computer make your partitions of the type ext4. If you use windows dual-boot use NTFS.

Mounting works with the configuration file in /etc/fstab. You'll have to edit this file as super user.
```
sudo gedit /etc/fstab
```

For the format have a look at:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

