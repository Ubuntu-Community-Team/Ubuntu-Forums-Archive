---
title: "Dell DJ Pocket Not Recognized"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by InsanePenguin08 on 2005-12-01
When I plug in my Dell DJ Pocket through a USB port, it doesn't show up in the Places-->Computer explorer.  I know that the computer knows something's there, because if I type ```
lsusb
``` into the Terminal, it shows up like this:```
eric@linux-box:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 010: ID 041e:4127 Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000

```
The Creative Technology, Ltd. doesn't show up unless it's plugged in, so I assume that it is the player.

I'd really like to get all of my music back onto my computer (I switched from Windows,) any help?

Oh, and if you guys know any good media players, lemme know how to get them, if you would.

Thanks

---

### Post by aysiu on 2005-12-01
You may have to manually mount it or add it to your /etc/fstab.
Can you post the output of the following commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by InsanePenguin08 on 2005-12-01
Sure

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

```
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  1.8G   33G   6% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  113M  10% /lib/modules/2.6.12-10-386/volatile
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

That's with the Dell DJ connected, if it makes any difference.  I don't think it does, but, eh.

---

### Post by aysiu on 2005-12-01
[QUOTE=InsanePenguin08]
That's with the Dell DJ connected, if it makes any difference.  I don't think it does, but, eh.[/QUOTE] No, it makes a big difference. I'm not seeing your Dell DJ anywhere. ```
sudo fdisk -l
``` should list all attached devices, hard drives, and partitions, regardless of whether they're mounted properly or not.

For example, when my external hard drive is plugged in, this is what mine looks like ```
sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       18494   133202947+   f  W95 Ext'd (LBA)
/dev/hda3           18495       19457     7735297+  83  Linux
/dev/hda5            1912       14763   103233658+   b  W95 FAT32
/dev/hda6   *       14764       16434    13422276   83  Linux
/dev/hda7           18363       18494     1060258+  82  Linux swap / Solaris
/dev/hda8           16435       18362    15486628+  83  Linux

Partition table entries are not in disk order

Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19929   160079661    c  W95 FAT32 (LBA)
``` External USB devices (my Sandisk player, my wife's iPod) generally show up as /dev/sda1 or /dev/sde1 or /dev/sdb1. This is even if they're not mounted--just if they're physically connected.

---

### Post by InsanePenguin08 on 2005-12-01
You spoke before of adding it to my /etc/fstab/?  How exactly would I go about doing that, and/or what would it do?

---

### Post by aysiu on 2005-12-01
[QUOTE=InsanePenguin08]You spoke before of adding it to my /etc/fstab/?  How exactly would I go about doing that, and/or what would it do?[/QUOTE] Unfortunately, you can't really do that unless you know where it's located. For example, an /etc/fstab entry might look like: ```
/dev/sda1  /delldj  vfat   umask=000    0   0
``` However, it's not at /dev/sda1. It doesn't appear to be anywhere...

---

### Post by InsanePenguin08 on 2005-12-01
Oh.  Damn.  

Well, I'm getting another computer in the next couple months anyways, and by then I'll learn to (successfully, I accidently deleted my whole hdd this time) dual-boot that system with Windows and Linux.  Until then..guess I have to use my mom's iPod that just sits there, unused.

---

