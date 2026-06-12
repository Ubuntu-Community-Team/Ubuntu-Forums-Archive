---
title: "[SOLVED] DD, wanted to make sure command doesn't spell destruction"
date: 2008-08-17
forum: General Help
---

### Post by jerome1232 on 2008-08-17
I'm just making sure this is doing what I think and want, I got the command off of this site [http://www.linuxweblog.com/dd-image](http://www.linuxweblog.com/dd-image) and looked at the man pages it seems correct to me.

Currently in a live cd environment

I'm wanting to image my entire drive (251GB) then compress it and send it over to my usb drive (160GB) I hope it fits :(

```
dd if=/dev/sda conv=sync,noerror bs=1k | bzip2 -c > /media/disk-2/sda.img.bz2
```

for restoration 

```
bzcat /media/<usb disk>/sda.img.bz2 | dd of=/dev/sda bs=1k
```

The guide also says to create a text file with partition info using the command below, and using this text file you can restore a specific partition.

```
fdisk -l /dev/sda > /media/<usb drive>/sda_fdisk.info

```

so my fdisk -l looks like this
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd300d300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    5  Extended
/dev/sda5               1        3039    24410704+  83  Linux
/dev/sda6            3040        3101      497983+  82  Linux swap / Solaris
/dev/sda7            3102       30515   220202923+  83  Linux

```
Then to restore sda5 I would do this. This command just doesn't look right to me (of=/tmp/sda5.img should be /dev/sda5 shouldn't it?)
```
bzcat /<path to usb disk>/<sda.img.bz2> | dd of=/dev/sda5 bs=512 skip=1 count=$[3039-1]
```

edit: second look I guess I just pretend sda1 doesn't exist and don't skip ahead (30515 is the end of my drive)

another edit: On further review it looks like it's better to use bs=1k, so I have edited my commands to reflect that.

I found a small usb drive to test all the commands on and everything is working fine except I can't figure out how to restore a single partition from the full drive image, only the whole drive. 

If anybody knows the correct way to grab a single partition out of the whole drive image feel free to chime in. I'll keep googling meanwhile.

---

### Post by jerome1232 on 2008-08-17
*bump*

I'm trying to figure out how to get a single partition out of the full drive image, (say I just wanted to restore sda7 which is my /home)

All tests on my 512 thumb drive have resulted in a corrupt partition.

I created two partitions on it, put files on both partitions and created an image. Then I deleted the files on one partition, unmounted the disk and tried a few variances on the above command, all resulted in corrupting the partition I was attempting to restore.

---

### Post by caljohnsmith on 2008-08-17
> **jerome1232 said:**
> 
```
dd if=[COLOR="Blue"]/dev/sda[/COLOR] conv=sync,noerror [COLOR="Blue"]bs=1k[/COLOR] | bzip2 -c > /media/disk-2/sda.img.bz2
```
First of all, I wouldn't think you would want to use a block size of "1k", because that is 1000 bytes; you should use factors of 512 to do your copying, since 512 bytes is the sector size used on your HDD. In that tutorial they use 64K, which is 64 X 1024 bytes (a multiple of 512), whereas 64k is 64,000 bytes. So the uppercase K makes a big difference.

Also, the input to the dd command above is your entire HDD: /dev/sda. Thus you get an image of the entire HDD. So unless you know of some special program that can search through that entire HDD image and pick out just the partition you want to restore, you can only restore the entire HDD image and not just a partition with the command above.

To restore just a partition (like sda5), the first step would be to have dd copy only the partition with:
```
dd if=[COLOR="Blue"]/dev/sda5[/COLOR] conv=sync,noerror [COLOR="Blue"]bs=1K[/COLOR] | bzip2 -c > /media/disk-2/sda5.img.bz2
```
Then to restore it, I believe all you would have to do is:
```
bzcat /media/<usb disk>/sda5.img.bz2 | dd of=[COLOR="Blue"]/dev/sda5 bs=1K[/COLOR]
```

---

### Post by jerome1232 on 2008-08-17
Thanks for the info about bs. I will adjust my tomboy notes accordingly.

I did realize that I was imaging the whole drive. From one of the comments on that guide they said you could make an image of the entire drive, and from that image produce an image of one of the partitions. So I was trying to do that, but instead of making a second image (of just the partition) just restore that portion (do I make any sense?)

But then I was using bs=1k so that may have been why mine failed. 

> If the sector size of partitions are known, you can extract partition images from the main image via:

# fdisk -l -u /dev/sda

Outputs as:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16771859     8385898+  8e  Linux LVM
/dev/sda2        16771860    75489434    29358787+  8e  Linux LVM
/dev/sda3        75489435    75698279      104422+  83  Linux
/dev/sda4        75698280   117210239    20755980    5  Extended
/dev/sda5        75698343   117210239    20755948+  8e  Linux LVM

So to create an image of the second partition (sda2) from existing image of sda...

# dd if=/path/to/sda.img of=/tmp/sda2.img bs=512 skip=16771860 count=$[75489434-16771860]


---

### Post by caljohnsmith on 2008-08-17
OK, I should have read that tutorial you linked to more carefully about how to restore just the partition from the HDD image using the info from fdisk--makes total sense now, so I stand corrected. :)

I think you should try it like this, and also be sure to do it as root, as I'm not sure if you did that previously:
```
sudo dd if=/dev/sda conv=sync,noerror [COLOR="Blue"]bs=512[/COLOR] | bzip2 -c > /media/disk-2/sda.img.bz2
```
But now it is really important that you use:
```
sudo fdisk -lu
```
Add the "u" option to fdisk so that fdisk will report its results in units of 512 bytes, which will exactly match the block size used above in dd. That way it will be a piece of cake restoring your partition like they show in the tutorial. For example:
```
john@TECH5321:~$ [COLOR="Blue"]sudo fdisk -lu[/COLOR]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81920159    40960048+   7  HPFS/NTFS
/dev/sda2        82043955   123620174    20788110   83  Linux
/dev/sda3       154336455   156296384      979965   82  Linux swap / Solaris
/dev/sda4       123620175   154336454    15358140    5  Extended
[COLOR="Blue"]/dev/sda5[/COLOR]       [COLOR="Red"]123620238[/COLOR]   [COLOR="DarkOrchid"]154240064[/COLOR]    15309913+  83  Linux
/dev/sda6       154240128   154336454       48163+  83  Linux

Partition table entries are not in disk order
```
So if I want to restore [COLOR="Blue"]sda5[/color] for example, I would do:
```
bzcat /<path to usb disk>/<sda.img.bz2> | sudo dd of=[COLOR="Blue"]/dev/sda[/COLOR] bs=512 skip=$[[COLOR="Red"]123620238[/color]-1] count=$[[COLOR="DarkOrchid"]154240064[/color]-[COLOR="Red"]123620238[/color]+1]
```
Important points:
[list]
[*]Make sure the output file for dd is the HDD (sda), and not the partition itself (sda5). In other words, use "of=/dev/sda" like above. The "skip" and "count" options will make sure the partition will be copied to the correct partition sda5 on the HDD.
[*]Also note that "skip" uses the fdisk start block for *sda5 minus one*. That's because "skip" tells dd how many blocks to skip, so if you use just skip=123620238 in the above example, dd will actually start writing at the next sector, and not actually start at 123620238. I think the tutorial missed that point.
[*]And lastly, be careful to note that "count" uses stop-start+1. That is because, if say sda5 were to start at sector 1, stop at sector 2, you want to copy *both* sectors. Thus in that case count=stop-start+1=2-1+1=2, so you will copy 2 sectors and not just the first one.
[/list]

---

### Post by jerome1232 on 2008-08-17
Thanks very much I'm off to help move furniture in and then test all this out on my poor usb disk again. :) And yes I've been running all this after doing a sudo -i to get a root prompt.
 I'll go ahead and mark it as solved.

---

### Post by jerome1232 on 2008-08-18
Awesome I made a typo while testing, instead of sdb2 a partition on my usb drive i'm using to test, I hit sda7 (my /home)! Thank goodness I have everything on dvd-r's! I was thinking about repartition anyways.

```
 fdisk -lu /dev/sdb

Disk /dev/sdb: 503 MB, 503709696 bytes
255 heads, 63 sectors/track, 61 cylinders, total 983808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000199ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      289169      144553+   6  FAT16
/dev/sdb2          289170      979964      345397+  83  Linux
[B]root@desktop:~# bzcat /media/disk-2/sdb.img.bz2 | dd of=[color="red"]/dev/sda7[/color] bs=512 skip=$[289169] count=$[979964-289171]
175224+0 records in
175224+0 records out
89714688 bytes (90 MB) copied, 4.45571 s, 20.1 MB/s[/B]
[COLOR="Red"]oops... thank god I have backups of sda7 on dvd-rw's maybe I'll try out some file recovery programs just to learn them[/COLOR]
```

---

### Post by caljohnsmith on 2008-08-18
Jerome1232, sorry, I made a big mistake in my last post: to restore your partition back to the HDD, the dd command should use sda (your HDD) and not the partition sda5. That's because the "skip" and "count" options will make sure the sda5 partition will be copied back to the correct place on the HDD. I edited that post and fixed the error.

**IMPORTANT EDIT:** When I wrote that previous post about restoring the partition sda5, I forgot you are not really trying to restore it back to your HDD--you are actually trying to image your entire HDD to your USB stick. So first of all, keep in mind that even if you start with a freshly formatted USB stick and try to copy just your HDD's sda5 partition to your USB, that certainly won't work as the USB stick won't even have the correct partition table set up in its master boot record. Also, I'm not sure even copying over your entire HDD image to your USB would work unless your HDD and USB stick are exactly identical in size, because the partition table carries data about how big the HDD is. But maybe it would work--you can always try; just make sure then you replace /dev/sda with your USB device name in the dd restore command so it writes to your USB and not your HDD.

---

### Post by jerome1232 on 2008-08-18
Oh sorry I guess I wasn't clear, right now I'm not imaging my actual HDD, I'm testing commands by imaging my tiny 512 MB usb stick (sdc), and restoring said stick then seeing if files are there and partitions are in good shape. I just made a typo earlier as all of my notes are written for the real task and restored my thumb disk to my actual /home partition. No worries I keep backups. :)

Moral of the story is don't play with dd when it's 1:38 am

okay well I've tested your edited command and it's still corrupting the partition table for me.

```
root@desktop:~# fdisk -lu /dev/sdc

Disk /dev/sdc: 503 MB, 503709696 bytes
255 heads, 63 sectors/track, 61 cylinders, total 983808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000199ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63      530144      265041    6  FAT16
/dev/sdc2          530145      979964      224910   83  Linux

root@desktop:~#bzcat /mnt/backup/sdc.img.bz2 | dd of=/dev/sdc bs=512 skip=$[530144] count=$[449820]
449820+0 records in
449820+0 records out
230307840 bytes (230 MB) copied, 118.652 s, 1.9 MB/s
root@desktop:~# fdisk -lu /dev/sdc

Disk /dev/sdc: 503 MB, 503709696 bytes
16 heads, 61 sectors/track, 1008 cylinders, total 983808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

I don't have time to vary try the command in different ways atm my wife is nagging me to finish painting. I think my command was correct. I tried it with a count of 449819 and that corrupted the partition table as well.

If I do a full restore the disk works fine so I know the image isn't corrupted. I will test more things out soon.

When I do this for real, it will be like this:
image sda -> sdb (sdb is usb disk)
restore img of sda on sdb -> sda

---

### Post by caljohnsmith on 2008-08-18
Jerome1232, I think I figured out the problem after reading the dd manual. The dd used in the restore command is reading the partition correctly from the image file by using the "skip" and "count" options, but *the skip option is only for the input, not output of the dd command*. So when you did:
```
bzcat /mnt/backup/sdc.img.bz2 | dd of=/dev/sdc bs=512 skip=$[530144] count=$[449820]
```
It took the sda2 partition and wrote it to the beginning of your USB drive sdc. So instead you would do:
```
bzcat /<path to usb disk>/<sda.img.bz2> | sudo dd of=/dev/[COLOR="Red"]sdc[/COLOR] bs=512 skip=$[Start-1] [color="red"]seek=$[Start-1][/COLOR] count=$[Stop-Start+1]
```
And that will copy your sdc2 partition back to the correct place. Or if things are not so corrupt that fdisk still shows the sdc2 partition still exists, the easiest way to restore sdc2 would be:
```
bzcat /<path to usb disk>/<sda.img.bz2> | sudo dd of=/dev/[COLOR="Red"]sdc2[/COLOR] bs=512 skip=$[Start-1] count=$[Stop-Start+1]
```
So I think my initial inclination of using sdc2 was actually correct. ;) Let me know if those work.

---

### Post by jerome1232 on 2008-08-18
Yeah I was just going over the dd man page and saw the skip/seek too. I can't test right now but will post back when I can. Thanks for the help!

---

### Post by jerome1232 on 2008-08-18
and, drum roll...........

It works, I really like this method of backing up! note the # prompt means I'm running these as root.

I did use a count of [end-start] though. When I used [end-start+1] it corrupted the partition table.

```
~# bzcat /mnt/backup/sdc.img.bz2 | dd of=/dev/sdc bs=512 skip=$[530144] seek=$[530144] count=$[449819]
```
and alternatly (both accomplish the same task)
```
~# bzcat /mnt/backup/sdc.img.bz2 | dd of=/dev/sdc2 bs=512 skip=$[530144] count=$[449819]
```

Thanks a bunch, not only do I know it works but I know why it works.
Before imaging it helps the compression to fill each mounted partition with zeros
```
~# dd if=/dev/zero of=/media/disk/delme && rm delme
~# dd if=/dev/zero of=/media/disk-2/delme && rm delme
```

note: In order to restore individual partitions, partitioning scheme MUST be already in place. When imaging be sure to dump the contents of fdisk to assist in restoring.
```
~# fdisk -lu /dev/sdc > /mnt/backup/fdisk-lu-sdc
```

---

### Post by caljohnsmith on 2008-08-18
> **jerome1232 said:**
> I did use a count of [start-end] though. When I used [start-end+1] it corrupted the partition table.

I'm glad you finally got it working. :) But I don't understand at all how using count=$[end-start+1] would have corrupted your partition table. If [end-start] is actually correct, then all [end-start+1] would do is copy over an extra sector at the end of the partition, which dd is reading from your image file; so that sector should be the same as the original. 

Just as a really simple example, if dd uses count=1, it copies 1 block. Say we have a file that starts at block 5 and ends at block 7, then it takes up 3 blocks: 5, 6, and 7. So to copy all three blocks count=stop-start+1. Anyway, if you figure out why it's not stop-start+1 please let me know. :)

---

### Post by richud on 2011-06-04
don't take 1 from the start sectors/blocks !!

if your partition starts at 2048, then use skip=2048 else it won't work.
count = 16775167 - 2048 + 1 = 16773120

e.g.

$ fdisk -l -u file.raw
You must set cylinders.
You can do this from the extra functions menu.

Disk file.raw: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088f0b

   Device Boot      Start         End      Blocks   Id  System
file.raw1   *        2048    16775167     8386560   83  Linux
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(1044, 52, 32)
$ dd if=file.raw of=test.raw skip=2048 count=16773120  bs=512
16773120+0 records in
16773120+0 records out
8587837440 bytes (8.6 GB) copied, 281.952 s, 30.5 MB/s
$ sudo mount -o loop test.raw /mnt/tmp
[sudo] password for rfm6: 
$ ls -al /mnt/tmp
total 100
drwxr-xr-x 21 root root  4096 2011-06-03 21:01 .
drwxr-xr-x  4 root root  4096 2011-06-03 22:06 ..
drwxr-xr-x  2 root root  4096 2011-06-03 20:59 bin
drwxr-xr-x  3 root root  4096 2011-06-03 21:02 boot
drwxr-xr-x  4 root root  4096 2011-06-03 20:52 dev
drwxr-xr-x 87 root root  4096 2011-06-03 21:12 etc
...

Now hexedit -s /dev/loop0 and look at how far down stuff is, it will probably be a page of zero's to begin with, find something to use as a marker and look at the byte position.


Now convert 2048 into bytes = 2048 x 512 = 1048576 to use with mount.
mount the original raw file
sudo mount -o loop,ro,offset=1048576 file.raw /mnt/tmp

Now again 
hexedit -s /dev/loop0
again scroll down and you will see at the same offset is the same data as expected.

If you try what the above comments suggest, taking one from the start for the skip, i.e.
dd if=file.raw of=test2.raw skip=2047 count=16773120  bs=512
then you will find it wont be mountable.....


$ sudo mount -o loop test2.raw /mnt/tmp
mount: you must specify the filesystem type


Also you can change it away from 512byte chunks too
e.g.

$ dd if=file.raw of=test.raw skip=1 count=8190 bs=1M
8190+0 records in
8190+0 records out
8587837440 bytes (8.6 GB) copied, 279.598 s, 30.7 MB/s
$ sudo mount -o loop,ro test.raw /mnt/tmp
$ ls -al /mnt/tmp
total 100
drwxr-xr-x 21 root root  4096 2011-06-03 21:01 .
drwxr-xr-x  4 root root  4096 2011-06-03 22:06 ..
drwxr-xr-x  2 root root  4096 2011-06-03 20:59 bin
drwxr-xr-x  3 root root  4096 2011-06-03 21:02 boot
drwxr-xr-x  4 root root  4096 2011-06-03 20:52 dev

---

