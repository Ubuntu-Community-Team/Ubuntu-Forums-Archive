---
title: "Mounting USB NTFS drives"
date: 2010-03-27
forum: Hardware
---

### Post by srajama on 2010-03-27
I am trying to mount an NTFS USB drive. I am able to connect a FAT32 drive to the same port, so I am sure it is not the port. I have installed ntfs-3g.

Now when I run fdisk, I get:

```

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005519e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37595   301981806   83  Linux
/dev/sda2           37596       38913    10586835    5  Extended
/dev/sda5           37596       38913    10586803+  82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


```

Next I tried mounting the drive

```

sudo mount /dev/sdb /media/external_ntfs/ -t ntfs-3g
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

If I understood this correctly, /dev/sdb is a 'device' whereas there should be a '/dev/sdb1' which is 'partition' which can be mounted. However, I do not see any partitions under /dev/sdb1 etc under /dev. 

What am I missing here?

---

### Post by new_tolinux on 2010-03-27
You want to link/mount the partition, not the main drive.
Try using /dev/sdb1 instead of /dev/sdb

---

### Post by coffeecat on 2010-03-27
> **srajama said:**
> I am trying to mount an NTFS USB drive. I am able to connect a FAT32 drive to the same port, so I am sure it is not the port. I have installed ntfs-3g.

Automount of external ntfs drives works out of the box. You don't need to install anything.

But here's your problem:


> **srajama said:**
> ```

sudo fdisk -l

<snip>


Disk /dev/sdb doesn't contain a valid partition table


```

Unless you edit the partition table or reformat that device, you won't be able to mount anything.

---

### Post by srajama on 2010-03-28
It looks like it could be a blown hard drive. I am running testdisk on the device to see if I can recover at least some data off the drive. I'll see how this goes. 

Any suggestion on utilities other than testdisk to run on this drive?

---

### Post by srajama on 2010-04-04
I tried running testdisk and both quick search and deep search are not showing me any partition data. 

At this point I am mostly interested in recovering a few folders off the drive. Is there any way I tool by which I can do something like this - "assume NTFS and read disk" ?

---

### Post by coffeecat on 2010-04-04
Part of testdisk is the Photorec recovery utility which can find and recover certain data files (not just photos). From the package description:

> PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)You'll have to search the forums/google for a howto. It's a bit fiddly and it's been a long time since I used it, so I don't want to mislead you with misremembered information. It's very good, but be warned: the recovered files do not have their original names. You'll get (possibly) many thousands of files in dozens of folders all with incomprehensible filenames.

---

### Post by srajama on 2010-04-04
Thanks for the tip - I did not know photorec could run on a unformatted volume like this! Very cool!

I'll know how it goes in another 4 hrs and 21 mins...

---

