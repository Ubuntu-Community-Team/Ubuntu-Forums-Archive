---
title: "Is my USB flash drive dead?"
date: 2012-06-28
forum: Hardware
---

### Post by forbajato on 2012-06-28
My daughter stores her homework on a USB flash drive.  Yesterday when we plugged it in to her laptop it didn't auto mount.  When I plug it in I get the following lines output from dmesg:
```
[13934.564565] scsi 7:0:0:0: Direct-Access              USB DISK 28X     1.00 PQ: 0 ANSI: 0 CCS
[13934.565639] sd 7:0:0:0: Attached scsi generic sg3 type 0
[13934.568204] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```
That is it, none of the other lines show up.  

Running Gparted gives nothing, it can't see the drive.  lsusb gives this:
```
Bus 001 Device 005: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive

```
So it looks like the system can see the drive but doesn't even go so far as to figure out the partition table on it.

Any ideas of what I can do (other than to use this as a teaching opportunity with my daughter to reinforce the importance of backups)?

thomas

---

### Post by ahallubuntu on 2012-06-29
In a terminal window, with the thumb drive plugged in, type

```
sudo fdisk -l

```

I still wouldn't be surprised if it has failed.  I've had a number of failed USB flash drives come my way.  They can easily fail for various reasons such as being zapped by ESD (ElectroStatic Discharge).

---

### Post by lrcaballero on 2012-06-29
Have you try it on a Windows PC? Also, try it while running a live CD. Good Luck.

Cheers

---

### Post by forbajato on 2012-06-29
Thanks for the input - the fdisk doesn't give any results for /dev/sdc disks even though sdc is identified (in part) in the dmesg output.

I suppose that means the disk is dead?

thomas

---

### Post by ahallubuntu on 2012-06-29
As suggested above, try it in another computer, perhaps a Windows PC.  If it doesn't show up there either...yes, I imagine it's dead.

---

### Post by forbajato on 2012-06-29
Thanks for the help - seems nothing can read this thing, time for the tinker bag (my number two daughter likes to take things apart!).

thomas

---

