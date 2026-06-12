---
title: "Resize swap partition on /dev/mapper"
date: 2013-10-20
forum: Hardware
---

### Post by Damwdan on 2013-10-20
Hello,

I own a very recent Sony Vaio Pro 13 that came with Windows 8 and I very recently installed Ubuntu as dual-boot. I managed to do that using the [trial and error method]("https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error") and had to do it this way because of UEFI and all the problems that came with it. Anyways, it worked a charm, until I realized I had done a mistake. During the installation process, I accidentally set my swap partition to about 4GiB while I have 8GiB of RAM. Therefore, when I tried to hibernate and resume today, it crashed and I couldn't log in (see [login loop]("http://askubuntu.com/a/360363")) and when I finally managed to log in, an error message popped telling me that the system had not been capable of resuming from hibernation. I only suppose that it happened because of the swap partition being to small, but I'm not sure. Anyways, I thought I would just resize it, shrinking the /home partition a little (I really don't need that much space), but when I opened GParted, I couldn't find the swap partition. I believe it was on /dev/sda7 when I installed it, but now it says the filesystem is unknown. I checked online and found possible solutions, one of them being that it's unknown because I chose to encrypt my home folder during the installation.

Anyways, I don't really know how to fix this problem, any help would be much appreciated.

Some useful partition data:

```
$[damwdan:~]% cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=702fa0a4-2ac9-4375-ad06-410e4c62bf60 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
#UUID=5417-5477  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda9 during installation
UUID=4f0cb439-5602-4588-856a-cc2f6575067f /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=cd90cf1d-a9aa-4669-ae6f-4ba5a1aecd90 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=5417-5477    /boot/efi    vfat    defaults    0    1
```

```
$[damwdan:~]% free -m
             total       used       free     shared    buffers     cached
Mem:          7892       3755       4137          0         71       1344
-/+ buffers/cache:       2339       5553
Swap:         3814          0       3814
```

```
$[damwdan:~]% blkid 
/dev/sda1: LABEL="SONYSYS" UUID="2E7F-45D5" TYPE="vfat" 
/dev/sda2: LABEL="Windows RE tools" UUID="46BE125ABE1242BB" TYPE="ntfs" 
/dev/sda3: UUID="5417-5477" TYPE="vfat" 
/dev/sda5: UUID="3AD81810D817C951" TYPE="ntfs" 
/dev/sda6: LABEL="Recovery" UUID="4EF25D4AF25D3783" TYPE="ntfs" 
/dev/sda8: UUID="702fa0a4-2ac9-4375-ad06-410e4c62bf60" TYPE="ext4" 
/dev/sda9: UUID="4f0cb439-5602-4588-856a-cc2f6575067f" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="1b2d7dd5-89d3-4be3-890c-b1dc6206f6db" TYPE="swap" 
```

I checked also this file and the UUID doesn't seem to be the same :

```
$[damwdan:~]% cat /etc/initramfs-tools/conf.d/resume 
RESUME=UUID=73dde4e0-2544-4661-9a56-42d40e8b1b32
```

And finally, GParted screenshot : [screenshot]("http://uploads.damwdan.com/perso/gparted.png")

I should mention: I have a SSD and I did not try to boot Windows after hibernation. EDIT: and I use Ubuntu 13.10

Thank you!

---

