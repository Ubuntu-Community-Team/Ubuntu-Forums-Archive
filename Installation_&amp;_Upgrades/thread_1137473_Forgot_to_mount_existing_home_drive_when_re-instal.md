---
title: "Forgot to mount existing /home drive when re-installing Ubuntu"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2009-04-25
When reinstalling Ubuntu, I forgot to mount my existing /home drive.

Right now, this is my fdisk:

```
$ sudo fdisk -l

Disk /dev/sda: 30.8 GB, 30816608256 bytes
255 heads, 63 sectors/track, 3746 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d78fd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        3746    20322225    5  Extended
/dev/sda5            1217        3648    19535008+  83  Linux
/dev/sda6            3649        3746      787153+  82  Linux swap / Solaris
```

So my question is, how can I destroy my existing /home directory and mount it with /dev/sda5

I'm pretty good with coding and Bash but have never really worked with fstab.

Thanks!

---

### Post by Tim Sharitt on 2009-04-25
You should have no problem mounting your old home partition over the current home.

Just add something like
```
/dev/sda1 /homet ext3 nodev,nosuid 0    2
```
to /etc/fstab, substituting the correct block device, fs type, etc.

Removing the data in the current home directory is optional, once the your home partition is mounted at /home, you will not see it.

I actually kept the pre-installed home directory intact so if I ever have a major problem with my configuration, I can just unmount the separate partition and boot with pristine user settings. :)

---

### Post by altonbr on 2009-04-25
That was perfect, thank you :)

---

