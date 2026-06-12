---
title: "grub-install to usb help"
date: 2008-08-06
forum: General Help
---

### Post by x20mar on 2008-08-06
Hi there,

I'm trying to install linux onto a usb pendrive and the last command to do this should be like

```
sudo grub-install --root-directory=/media/disk /dev/sdb
```

The problem lies every time I try it whether it's sda, sda1, ... sdc... I always get the following messages:

```
mint alpha # grub-install --root-directory=/media/disk /dev/sda
/dev/mmcblk0p1 does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/sda1
/dev/mmcblk0p1 does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/sda2
/dev/mmcblk0p1 does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/sdc
/dev/mmcblk0p1 does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/sdb
/dev/sdb does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/mmcblk0p1
/dev/mmcblk0p1 does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/mmcblk0
/dev/mmcblk0 does not have any corresponding BIOS drive.
mint alpha # grub-install --root-directory=/media/disk /dev/usb
/dev/usb does not have any corresponding BIOS drive.
mint alpha # grub-install --recheck /dev/sdc
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
mint alpha # grub-install --recheck /dev/sdc1
Probing devices to guess BIOS drives. This may take a long time.
/dev/sdc1: Not found or not a block device.
mint alpha # grub-install --recheck /dev/sdc2
Probing devices to guess BIOS drives. This may take a long time.
/dev/sdc2: Not found or not a block device.
mint alpha # grub-install --recheck /dev/sdc3
Probing devices to guess BIOS drives. This may take a long time.
/dev/sdc3: Not found or not a block device.

```

Now the main cause for all of this, properly lies in the fact I'm doing this from a Live CD (since my laptop runs in vista)

I had a look at fdisk -l and I pulled up the following.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1f91a28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       24322   193822720    7  HPFS/NTFS

Disk /dev/sdc: 515 MB, 515899392 bytes
16 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     1935435     2484263   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(1935434, 6, 59)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(2484262, 2, 23)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     1340912     1884235   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(1340911, 7, 57)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(1884234, 5, 52)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      543337     1952977   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(543336, 1, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(1952976, 1, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   *     1405875     1405897       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(1405874, 10, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(1405896, 2, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/mmcblk0: 2040 MB, 2040528896 bytes
29 heads, 28 sectors/track, 4908 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        4909     1992580+   6  FAT16

```

Any help on this would be greatly appreciated.

Many Thanks

---

### Post by Kobalt on 2008-08-06
If you want to create a Live USB stick there is a much more simple way, IMHO : [UNetbootin]("http://unetbootin.sourceforge.net/")

You can do it all straight from windows, you can choose among many Linux flavors and you can customize your Live USB...

---

### Post by matt.taylor on 2008-08-06
Some USB sticks don't all support a bootable iso / os. But for the life of i can't remember the damn term its called.](*,)

---

### Post by rEbyTer on 2008-08-06
Try to make it bootable with lilo.
Install it:
```
sudo apt-get install lilo
```
and then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

Then try to reinstall grub..

---

### Post by x20mar on 2008-08-06
> **Kobalt said:**
> If you want to create a Live USB stick there is a much more simple way, IMHO : [UNetbootin]("http://unetbootin.sourceforge.net/")

You can do it all straight from windows, you can choose among many Linux flavors and you can customize your Live USB...

Hi Kobalt,

I had a look at UNetbootin, and as useful as it is, it unfortunately doesn't help me with my problem, if only it could handle raw images.

Any other suggestions?

---

### Post by x20mar on 2008-08-06
> **rEbyTer said:**
> Try to make it bootable with lilo.
Install it:
```
sudo apt-get install lilo
```
and then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

Then try to reinstall grub..

Hi rEbyTer,

I don't think that would work, as I said before I'm using a Live CD and not an actual installation.

---

### Post by Kobalt on 2008-08-06
You mean you're trying to install a whole system on your USB drive, not just a Live environment in order to perform an install on a hard drive ?

---

### Post by x20mar on 2008-08-06
> **Kobalt said:**
> You mean you're trying to install a whole system on your USB drive, not just a Live environment in order to perform an install on a hard drive ?

Hi Kobalt,

yeah that sounds about right. It's not a big one only 256MB!

---

### Post by caljohnsmith on 2008-08-06
X20mar, when you run that grub-install command, first of all, are you sure your USB stick is mounted to /media/disk? Run the following to make sure:
```
mount
```
Also, whatever device is mounted to /media/disk will tell you what your correct USB device name is (/dev/sdc, etc). And if I remember correctly, I think you need to setup a /boot or /boot/grub folder on your USB stick prior to running the grub-install command, as I don't think the grub-install command creates a folder for you. I could be wrong about that, but it won't hurt to create those folders first:
```
sudo mkdir -p /media/disk/boot/grub
```
To get around those BIOS drive errors, often that can be overcome by forcing Grub to look for drives again:
```
sudo grub-install --root-directory=/media/disk /dev/sdX [COLOR="Red"]--recheck[/COLOR]
```
Let me know how it goes.

---

### Post by x20mar on 2008-08-06
> **caljohnsmith said:**
> X20mar, when you run that grub-install command, first of all, are you sure your USB stick is mounted to /media/disk? Run the following to make sure:
```
mount
```
Also, whatever device is mounted to /media/disk will tell you what your correct USB device name is (/dev/sdc, etc). And if I remember correctly, I think you need to setup a /boot or /boot/grub folder on your USB stick prior to running the grub-install command, as I don't think the grub-install command creates a folder for you. I could be wrong about that, but it won't hurt to create those folders first:
```
sudo mkdir -p /media/disk/boot/grub
```
To get around those BIOS drive errors, often that can be overcome by forcing Grub to look for drives again:
```
sudo grub-install --root-directory=/media/disk /dev/sdX [COLOR="Red"]--recheck[/COLOR]
```
Let me know how it goes.

Hi caljohnsmith,

Thanks for getting back to me. mount provides the following details:
```
mint@mint ~ $ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

```

so I assume that the final line should then be:
```
sudo grub-install --root-directory=/media/disk /dev/mmcblk0p1 --recheck

```

however that throws back to me
```
Probing devices to guess BIOS drives. This may take a long time.
/dev/mmcblk0p1 does not have any corresponding BIOS drive.

```

I'm really stuck here but I'm starting to think that means that my laptop cannot boot from there as there is no BIOS drives for it, so boot somewhere else. Is that right?

ps Yes I switched to a SD card, I think there was some issues with the usb drive I was using but the theory should all be the same.

UPDATE: I just tries this with an USB drive so mount gave
```
/dev/sdc1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

```

so the line would be
```
 sudo grub-install --root-directory=/media/disk-1 /dev/sdc1 --recheck

```

which worked! I guess it just wouldn't let me boot from an SD card!

Thanks for your help!

---

