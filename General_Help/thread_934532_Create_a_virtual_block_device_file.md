---
title: "Create a virtual block device file"
date: 2008-09-30
forum: General Help
---

### Post by ThaddeusW on 2008-09-30
Ok I need to do some tests with block devices but I dont want to use an actual disk. I need to know how I can create a "virtual" block device file so I can fdisk it and setup partitions etc. I then need to mount them using the loopback driver.

I tried this by first creating a blank file with dd from /dev/zero. Then fdisk the image but the file does not have cylinders so I edited the cylinders, sectors and heads in fdisk. For example I created a blank 128MB file and then used fdisk to change the cylinders to 504, heads to 8 and sectors to 62. this closely follows a 128MB compact flash card. After trying to write the new data it gives me error 25. Supposedly the kernel will use the new partition table on a reboot but that does not work.  

Any ideas? I could dump a small compact flash card block device and just play with that image but I want to do this from scratch.    

Any ideas?

---

### Post by marczis2 on 2010-05-14
Hi,
sorry its too late for me to give a detailed description, but here are the commands, read the manuals...

dd if=/dev/zero of=~/test.bin count=1000k  ==> create an empty file size ~512Mb

losetup /dev/loop0 test.bin ===> connect 0 loopback device to the file

cfdisk or fdisk /dev/loop0 ==> create the partition, tired with only one, I don't know what if you like more than one...

mkfs.ext2 or whatever u like ==> create the fs on the partition

mount /dev/loop0 /mnt/test ==> mount to the test directory...

so now, u have a device like a winchester, but its a file...

Hope it helped... 
Br.
   Peter.

---

### Post by AtomicClock on 2011-07-20
The guide by marczis is good. Just to add to it, if you want multiple loop devices, you can use the rest of /dev/loop*. If you need even more, you can create your own loop devices using

```
mknod /dev/loopNUM b 7 NUM
```

where NUM is the loop number. The important bit is the "b", which designates a block device, and the major number "7", designating a loop, and the minor number "NUM", which has to be a unique loop device number. Also, you don't have to create the device under /dev. You can make it anywhere you'd like, but it has to have a unique minor number, because when you use losetup it gets mapped to /dev/loopNUM automatically. So, for example:

```
$ mknod testlo b 7 20
$ losetup testlo test.bin
$ ls -l /dev/loop20
brw-rw---- 1 root disk 7, 20 Jul 20 10:44 /dev/loop20
```

---

