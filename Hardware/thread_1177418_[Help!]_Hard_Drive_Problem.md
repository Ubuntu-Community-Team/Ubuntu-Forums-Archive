---
title: "[Help!] Hard Drive Problem"
date: 2009-06-03
forum: Hardware
---

### Post by jamespayne on 2009-06-03
[B]Recently there's an unexpected power outage in our server room. When I tried to reboot the server, it complains that the root partition is not accessible. 

I did fsck, the output is:[/B]

```
myname@myserver:/mnt$ sudo fsck /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Invalid argument while checking ext3 journal for /
```[B]

Looks like superblock is corrupted. So I tried "sudo dump2fs /dev/sda5 | grep superblock" to search for alternative superblocks, but got nothing! [/B]

**I then tried some superblocks such as: 32768, 98304, 20480000, 23887872, etc., and got:**

```
myname@myserver:/mnt$ sudo fsck -b 23887872 /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
```[B]

I have no idea what to do now. Any suggestions?[/B]

BTW, I learnt from some internet posts that gpart can detect the partition of a disk. So I tried gpart. Below are the outputs, not sure if they are helpful. 

```
myname@myserver:/mnt$ sudo gpart /dev/sda5 
Begin scan...
End scan. 
Checking partitions...
Ok. 
Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r 
Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r 
Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r 
Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```


The output of fdisk is:

```
myname@myserver:/mnt$ sudo fdisk /dev/sda -l
 
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb29bb29
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2              63        8815    70308472+   5  Extended
/dev/sda5              63        8572    68356543+  83  Linux
/dev/sda6            8573        8815     1951866   82  Linux swap / Solaris
```

---

### Post by Drew Woodard on 2009-06-03
If you have the time and space I would use dd to copy that drive to an image file on another hard drive or network share so you can at least get back to your current position if stuff gets any more screwed up.

It might be worth giving the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") livecd a try if you haven't already and see if it detects a lost partition / inaccurate partition table.

---

### Post by jamespayne on 2009-06-03
> **Drew Woodard said:**
> If you have the time and space I would use dd to copy that drive to an image file on another hard drive or network share so you can at least get back to your current position if stuff gets any more screwed up.

It might be worth giving the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") livecd a try if you haven't already and see if it detects a lost partition / inaccurate partition table.

Thanks for the input. I will give TestDisk a try.

---

### Post by jamespayne on 2009-06-03
TestDisk doesn't work. No partition found. Any other suggestions?

---

### Post by Drew Woodard on 2009-06-04
> **jamespayne said:**
> TestDisk doesn't work. No partition found. Any other suggestions?

That's unusual but not unheard of, power failures can be nasty and cause all sorts of weird, difficult to reproduce problems if they happen at the wrong time.

One thing you could try is, assuming your superblock is trashed, is boot off an Ubuntu livecd and see if one of the backup copies can be found, using the directions [here]("https://www.redhat.com/archives/ext3-users/2003-July/msg00035.html") just in the paragraph that begins with "It looks like your block".

If that doesn't work you could try creating a partition of the same size in the same location that the original partition existed, reboot and do a fsck check on it.  Note that this is highly dangerous and it would be good if you had a dd image of the drive as a backup before trying something like that.  There is an example of the partition recreation technique [here]("http://ubuntuforums.org/showthread.php?t=343691").

If all that fails one thing you could do as a last resort is try [ext3grep]("http://groups.google.com/group/ext3grep/web/ext3grep-source-code-and-overview").  This is more a program for recovering accidentally deleted files on a still working system so ymmv.

---

### Post by jamespayne on 2009-06-05
> **Drew Woodard said:**
> That's unusual but not unheard of, power failures can be nasty and cause all sorts of weird, difficult to reproduce problems if they happen at the wrong time.

One thing you could try is, assuming your superblock is trashed, is boot off an Ubuntu livecd and see if one of the backup copies can be found, using the directions [here]("https://www.redhat.com/archives/ext3-users/2003-July/msg00035.html") just in the paragraph that begins with "It looks like your block".

If that doesn't work you could try creating a partition of the same size in the same location that the original partition existed, reboot and do a fsck check on it.  Note that this is highly dangerous and it would be good if you had a dd image of the drive as a backup before trying something like that.  There is an example of the partition recreation technique [here]("http://ubuntuforums.org/showthread.php?t=343691").

If all that fails one thing you could do as a last resort is try [ext3grep]("http://groups.google.com/group/ext3grep/web/ext3grep-source-code-and-overview").  This is more a program for recovering accidentally deleted files on a still working system so ymmv.

NONE of them work...

---

