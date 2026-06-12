---
title: "unable to boot after fresh install on Raid1 setup"
date: 2014-04-26
forum: Hardware
---

### Post by Heeter on 2014-04-26
Hi all,

This is for Ubuntu 14.04 Server 64bit.

Trying to install this onto a RAID1 2x750GIG setup. Intel onboard RAID. It installs successfully, sees the raid array during the install and applies the appropriate drivers, and then finishes the install.

then upon reboot, it cannot find the OS, it just tells me to insert a disk.

I checked the raid configuration, the boot order, and disabled all other bootable devices from the BIOS. 

Any other Ideas?

Thanks

Heeter

---

### Post by RAMChYLD on 2014-04-26
Did you tell the installer to install grub to /dev/mapper/whatever_your_raid_array_name_is instead of /dev/sda? Seems like a good bet that you picked the wrong place to install GRUB to and overlooked that option during install.

I've done that the first few times I installed Ubuntu onto a RAID array myself.

---

### Post by Heeter on 2014-04-26
Thanks for the heads up on that, RAMChYLD, I will look into that when I start my next reinstall right away..... I just kept hitting okay throughout the install.

Heeter

---

### Post by Heeter on 2014-04-26
Update

Well I tried to do what was mentioned above, I still could not get it to work,

So I resorted manually partitioning the RAID array.

That worked

Thanks

Heeter

---

