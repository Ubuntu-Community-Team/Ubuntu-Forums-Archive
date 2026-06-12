---
title: "Dual boot permantly corrupted windows"
date: 2008-10-09
forum: Hardware
---

### Post by slick666 on 2008-10-09
Dear Ubuntu Users.

I've run across a problem setting up a dual boot laptop that I've never encountered before and cannot seem to find any posts on.

The Laptop is a thinkpad R40e

What I did is the follwing.

1. Install windows (no updates, just install and boot into windows)
2. Install Ubuntu, split hd in two
3. Update Ubuntu.

The error I'm receiving now is the Blue screen of death every time I try to boot to windows. Since it's a fresh install I figured I may have messed it up with the repartitioning some how. So I popped int he windows install disk thinking I'll just reinstall grub later. Unfortunately the windows installer reports the error  "setup cannot access this disk." when it reaches the partitioner. and if I press any buttons it hits the blue screen of death.


Nothing I've done should really be messing with the windows installer. I popped in Gparted Live and was able to reformat the first partition as NTFS and ubuntu boots and works fine. 

What do you all think I'm missing to get windows back on this machine?

---

### Post by phidia on 2008-10-09
Open a terminal (from Applications > Accessories) enter > fdisk -l and post the output here.

What version of windows are you trying to re-install?

---

### Post by slick666 on 2008-10-10
Thanks for the Reply

The windows Version is XP Pro w/SP2

here is the fdisk -l

```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2197    17647371    7  HPFS/NTFS
/dev/hda2            2198        4864    21422677+   5  Extended
/dev/hda5            2198        4747    20482843+  83  Linux
/dev/hda6            4748        4864      939771   82  Linux swap / Solaris
```

Let me know your thoughts

---

### Post by slick666 on 2008-10-10
Also....

I found this link to a screen shot that has almost exactly the error I'm having in case anyone is confused.

[http://tools4arab.com/up/uploads/b28c26ff11.jpg]("http://tools4arab.com/up/uploads/b28c26ff11.jpg")

The only difference is the size of the HD but other than that it's exactly the same. From that screen if you start pressing keys (like up, down, D, etc. you get a BSOD.

---

### Post by slick666 on 2008-10-10
Update,

I ended up deleting the first NTFS Partition and now the installer shows that it found a 973 MB Partition of FAT32 :confused:

I think something about the way GParted is partitioning the hard drives is throwing windows off.

I'm going to wipe the thing clean with GParted and installing windows again but doing the partitioning in windows. See if it works that way.

Anyone ever heard of GParted messing with windows in this way?

---

### Post by slick666 on 2008-10-10
Update:

I deleted all partitions and windows installed fine. I poped in the ubuntu 8.04 Alternative Install CD and manually created two other partitions (root and swap) and installed Ubuntu.

Upon boot up windows got the BSOD again :mad:

I tried Ubuntu and it started up just fine. What I'm figuring is that somehow gparted is modifying the partition table in a way that Windows can't handle. So when windows sets up the partition table it's ok, but as soon as Ubuntu (or rather gparted) touches the partition table windows just blows up.

When I put in the windows install disk and walked through it the installer read the drive as one large partition. of type "unknown". It's size was the entire disk. I don't know what to make of that.

My thought is that Ubuntu (or more accurately gparted) is partitioning the drive in a way that windows doesn't like. My next move would be to do all the partitioning in windows and try to install ubuntu on the partitions provided by windows partitioner

---

### Post by slick666 on 2008-10-13
[bump]

Hey Guys Just to follow up. Partitioning with windows first **did** seem to work. I can boot Linus, and I can boot windows. I think it sucks that I can't seem to install it the same way Ive done before.

Does anyone have some thoughts as to what the problem is?

---

