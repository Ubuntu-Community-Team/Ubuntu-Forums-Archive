---
title: "new hard disk grub messed up"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by loonyjuice on 2008-12-12
Ok, I'm hoping this is going to be simple but here's the situation.

I have 5 hard disks (3 sata, 2 pata) and ubuntu was installed on /dev/sdc1. I've removed 1 pata drive (80GB) and installed a newer (1TB sata) drive instead. This is moved my /root drive to /dev/sdd1. So when I attempt to boot I get grub error 17.

So I do some searching and try to reinstall grub. I check devices.map and /root is hd3,0, which is fair enough. So in grub I do a root(hd3,0) setup(hd0) and reboot. I still get error 17.

I read some more that the hard disk order might have changed. Well, I have a go at re-arranging them so that, I think, they are in the right order. I then get error 5! Now I'm stuck on error 5.

here's some debugging:

**ubuntu@ubuntu:/media/disk/boot/grub$ sudo blkid**
/dev/sda1: LABEL="dump" UUID="2f034cf9-7bd1-41c4-b3aa-999981dac4ca" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="download" UUID="9244843e-5115-4cfa-9248-c3da274994ea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="8c9da04e-2121-4a2f-b5c2-3334848ddb59" TYPE="ext3" 
/dev/sdd5: UUID="30e28866-4055-4d6d-ae85-c483cde6dfb2" TYPE="swap" 
/dev/sde1: LABEL="music" UUID="3b3f48d1-7f0a-45cb-a2c5-ee31ab2d8115" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs"

**ubuntu@ubuntu:/media/disk/boot/grub$ sudo fdisk -l**

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e7cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xecebeceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006144

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       18707   150263946   83  Linux
/dev/sdd2           18708       19457     6024375    5  Extended
/dev/sdd5           18708       19457     6024343+  82  Linux swap / Solaris

Disk /dev/sde: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a79d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       36483   293049666   83  Linux

**ubuntu@ubuntu:/media/disk/boot/grub$ cat device.map** 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

Please can someone help me rectify this, or it's yet another reinstall :(

Thanks,

Martin

---

### Post by caljohnsmith on 2008-12-12
Most likely the reason you are getting the Grub error 17 is because you have Grub installed to the MBR (Master Boot Record) of sda while Grub's boot files are on sdd; but on start up, Grub sees the order of drives as the BIOS boot order, not as how the drives are ordered in /dev once you boot into Ubuntu. So in practical terms that means unless your drives in your BIOS boot order are exactly the same order as they are in Ubuntu (ie. sda, sdb, sdc, etc), then Grub will look on the wrong drive for the boot files and return a Grub error. Usually the easiest solution is to simply install Grub to the MBR of the Ubuntu drive and then set your BIOS to boot the Ubuntu drive. That way your drives are not dependent on each other for booting, and you won't have to worry about Grub errors resulting from having Grub's boot files on a different drive then the boot drive. 

To install Grub to the MBR of your Ubuntu drive, you would do:
```
sudo grub
grub> root (hd3,0)
grub> setup (hd3)
grub> quit
```
Reboot, set your BIOS to boot the Ubuntu drive, and you should get the Grub menu on start up. See if you can get that far or let me know if you run into problems. :)

---

### Post by loonyjuice on 2008-12-12
Amazing! That must be the one thing I hadn't tried. Thank you very much. I'm now typing this from my original ubuntu desktop and I don't have to spend all weekend reinstalling a lot of stuff.

---

### Post by caljohnsmith on 2008-12-12
Glad to hear that did the trick; cheers and have fun with your Ubuntu install. :)

---

