---
title: "RAID help"
date: 2009-11-28
forum: Hardware
---

### Post by sunrex on 2009-11-28
I'm planning on setting up a 4x500GB software RAID10 and having a 1TB backup HDD for the entire RAID array, I want grub installed on all four of the RAID HDD's in case one fails. That way it will boot up with no issues and I can replace the drive without worry of having to reinstall the entire thing.

For the 1TB backup drive, I want it off at all times accept when backing up or restoring - so how would I go about doing this?. I don't want the disk spinning or even operating unless those two conditions are met.

For the Grub, how would I go about doing this?. I followed this guide for centos raid: [http://www.flmnh.ufl.edu/linux/linux_software_raid.htm](http://www.flmnh.ufl.edu/linux/linux_software_raid.htm)

So, would I just do this?:

grub
> device (hd0) /dev/sda
> root (hd0,0)
> setup (hd0)
> device (hd1) /dev/sdb
> root (hd1,0)
> setup (hd1)
AND add the other two drives like so?.
>device (hd2) /dev/sdc
>root (hd2,0)
>setup (hd2)
>device (hd3) /dev/sdd
>root (hd3,0)
setup (hd3)

I don't know if that will work or not since I dont have the hard drives yet.. any ideas?.

Thank you!.

---

