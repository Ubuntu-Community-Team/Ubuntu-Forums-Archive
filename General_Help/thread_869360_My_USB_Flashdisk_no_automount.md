---
title: "My USB Flashdisk no automount"
date: 2008-07-24
forum: General Help
---

### Post by mTuran on 2008-07-24
i plug my flashdisk but it isn't auto mount. i must to mount manually please help.

---

### Post by ubockto on 2008-07-24
erm, had a "strange problem" with my usb devices, i couldnt figure how the hell it managed to see my usb keyboard and mouse, and yet refused to see my webcam and memory card reader, it was an option in my bios set at 2 usb devices and not at the max of 8, lol, maybe try there first, may work, dunno if it is the problem, if you are a bit weak with your pc bios, its best left to someone who does

---

### Post by koji042 on 2008-07-24
Can you go into the Terminal and type
```
sudo fdisk -l
```
and copy what you get here? I might be able to help you if I know what your USB Flash is being seen as by Ubuntu.

Also, you might want to look into fstab (automount configuration file basically):
[Ubuntu Documentation Page on fstab]("https://help.ubuntu.com/community/Fstab?highlight=(dmask)")
[How to fstab]("http://ubuntuforums.org/showthread.php?&t=283131")
and also
[How to mount filesystems in Linux]("http://www.tuxfiles.org/linuxhelp/mounting.html")

Hope this helps.

---

### Post by mTuran on 2008-07-26
> **koji042 said:**
> Can you go into the Terminal and type
```
sudo fdisk -l
```
and copy what you get here? I might be able to help you if I know what your USB Flash is being seen as by Ubuntu.

Also, you might want to look into fstab (automount configuration file basically):
[Ubuntu Documentation Page on fstab]("https://help.ubuntu.com/community/Fstab?highlight=(dmask)")
[How to fstab]("http://ubuntuforums.org/showthread.php?&t=283131")
and also
[How to mount filesystems in Linux]("http://www.tuxfiles.org/linuxhelp/mounting.html")

Hope this helps.

fdisk-l output is:

```
mturan@mturan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b9f2b9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19122   153597433+  83  Linux
/dev/sda2   *       19123       29455    82999296    7  HPFS/NTFS
/dev/sda3           29456       30401     7598745    5  Extended
/dev/sda5           29456       30401     7598713+  82  Linux swap / Solaris

Disk /dev/sdb: 4143 MB, 4143972352 bytes
255 heads, 63 sectors/track, 503 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x023bb126

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         504     4046816+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(502, 254, 63) logical=(503, 206, 23)

```

thanks

---

### Post by mTuran on 2008-07-26
> **ubockto said:**
> erm, had a "strange problem" with my usb devices, i couldnt figure how the hell it managed to see my usb keyboard and mouse, and yet refused to see my webcam and memory card reader, it was an option in my bios set at 2 usb devices and not at the max of 8, lol, maybe try there first, may work, dunno if it is the problem, if you are a bit weak with your pc bios, its best left to someone who does

no usb problem. ubuntu see USB flash disk but doesn't auto mount.

---

### Post by Jeremy23 on 2008-07-26
To see why it's not mounting, you can type this:

```
$ mkdir /tmp/flashdrive
$ sudo mount -t auto /dev/sdb1 /tmp/flashdrive
```

Then, see if there is an error. If no error, see if you can access your flash drive by navigating to /tmp/flashdrive in the file browser.

---

### Post by mTuran on 2008-07-26
i did it.. there is no error but not automounting because when i enter 

```
sudo mount -t auto /dev/sdb1 /tmp/flashdrive
```

this code, /dev/sdb1 changing to another one(like /dev/sde1 or /dev/sdd1)..

---

### Post by jonian_g on 2008-07-26
This made my flash drive to automount:

```
sudo apt-get install libxerces28
```

Plug it in and it should automount.

---

### Post by Jeremy23 on 2008-07-26
> **jonian_g said:**
> This made my flash drive to automount:

```
sudo apt-get install libxerces28
```

Plug it in and it should automount.
What the heck? That package doesn't do *anything* even *remotely* related to mounting flash drives. It's more likely a coincidence that it started working.

---

### Post by jonian_g on 2008-07-26
I don't know what exactly it does but if I remove it I can't mount 2 of my flash drives (cheap ones, unknown manufacturer) but I can mount my creative mp3 player.

---

