---
title: "Live CD doesn't see hard drive"
date: 2013-12-07
forum: Hardware
---

### Post by jord1981 on 2013-12-07
I have a hard drive onto which we back up all of our personal pictures and videos (Drive 2). It is a Seagate 2TB SATA drive.

I want to start making a quarterly back up of this drive on an identical Seagate 2TB SATA drive (Drive 3). I disconnected my boot drive (Drive 1) and replaced it with this Drive 3 for the purpose of secondary backup. I then attempted to boot with live cd to copy all files from Drive 2 to Drive 3. 

However, when I booted up, Lubuntu sees Drive 3 (connected to the first SATA connection) but does not see Drive 2 (connected to the second connection).  Lubuntu has no problem seeing Drive 2, when Drive 1 is connected and the system is booting from there.

Advice?

Thanks in advance.

---

### Post by Bashing-om on 2013-12-07
jord1981; Hi !

To my mind strange too .
Let's see if the disk utilities see the hard drives>
If they are partitioned legacy MBR (msdos); try:
```

sudo fdisk -lu

```
and more probably GPT partitioned: try:
```

sudo gdisk -l

```

Might also swap the cables around and see if the problem moves with the cables. Maybe isolate to a bad connection or bad cable (??)

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by jord1981 on 2013-12-08
Fdisk only sees Drive 3 (sda) and the USB drive I'm using to boot (sdb).

Gdisk was not installed.  When I installed the package, I got the following error:
> Problem openoing -l for reading! Error is 2.
The specified file does not exist!

FWIW the CMOS utility sees both 2 TB drives (Drive 2 and 3).

I'll try switching the cables and report back.

---

### Post by jord1981 on 2013-12-08
I am no longer able to boot the machine except when using drive 1.  See [http://ubuntuforums.org/showthread.php?t=2192404](http://ubuntuforums.org/showthread.php?t=2192404)

---

### Post by jord1981 on 2013-12-08
I was eventually able to boot from USB key and see both hard disks but the DVD drive disconnected.  Apparently 4 disks was too much to handle?

---

### Post by Bashing-om on 2013-12-08
jord1981; Youch !
Three things pop into my mind at this time.
a) Have you tried resetting bios to defaults with all drives hooked up ? Maybe bios will remap the drives .

b) Verify that the UUIDs of all partitions are correct, and none are duplicated, and all match up .
```

sudo blkid
cat /etc/fstab
mount

```
c) The use of "device.map" file has been depreciated, however, I had to use that file to get my system to boot properly, after I moved drives around. Took me forever to figure that one out !.
Does this file exist on your system:
```

ls -la /boot/grub/device.map
##and if it does exist:
cat /boot/grub/device.map

``` and let's see what the map file contains.

Might consider generating that file for the system to use.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

