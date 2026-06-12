---
title: "Hard drive crash"
date: 2008-11-24
forum: General Help
---

### Post by Jimmey on 2008-11-24
I was writing a DVD iso file to /media/sdb1 when my computer, for whatever reason, completely crashed.

Following the crash, it took a while to get the computer restarted again because the power button wasn't turning the computer on.

After a while of waiting, I finally managed to get the computer turned on, where during boot it reverted to an emergency root shell because a standard "FSCK" of /dev/sdb1 had failed.

I continued normal boot to find that /dev/sdb1, a standard IDE 250GB HDD, wouldn't, for love nor money, mount. Although when I ```
sudo disk -l
```

/dev/sdb1 is among the results that is returned, mounting, or even trying to run a manual FSCK, results in a failure.

```
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```

```
mount: special device /dev/sdb1 does not exist
```

EDIT: Running testdisk shows the partition and all of the files on there. 
The partition is marked as being primary bootable. Is that right? Or should it just be primary?

What should I do?

---

### Post by linux_tech on 2008-11-24
Is the device recognized in the bios?

---

### Post by psusi on 2008-11-24
It might help if you post the output of fdisk -l, and also check the output of dmesg for errors.

---

### Post by The Cog on 2008-11-24
I would be inclined to take an image of the disk to start with. **dd** should be able to do that. Then try either **fsck.ext3 /dev/sdb1** (if it was formatted ext3) or perhaps try what it suggests and do **e2fsck -b 8193 /dev/sdb1** and see if that helps.

---

### Post by Jimmey on 2008-11-24
I had tried both of those suggestions which returned the same results.

fdisk -l returned 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
```

Weirdly, it seemed as though the computer recognized there was a big lump of metal in there somewhere (sdb1) for something (storing files), but couldn't figure what; as trying to fsck with any of the stored superblocks didn't work - until I just got in.

Having left the computer for a little while, I just booted it fine with /dev/sdb1 mounting perfectly.

What could have caused this?

---

### Post by Cracauer on 2008-11-24
Your partition is there but the filesystem on the partition seems to be unhappy.

If there is important data on there, do not run fsck ever again. Run Linux from a fresh harddrive and connect this one read only.

What does this say?
`sudo cat /dev/md0 | file -`
`sudo cat /dev/md0 | hexdump | head`

(insert your disk device for md0)

Also post your /etc/fstab

---

### Post by psusi on 2008-11-24
Hrm... there should be at least 2 partitions; one for swap.

---

### Post by Jimmey on 2008-11-25
That's not the problem - The swap partition is on the first drive - 

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         653     5245191   83  Linux
/dev/sda2             654        4922    34290742+  83  Linux
/dev/sda3            4923        4998      610470    5  Extended
/dev/sda5            4923        4998      610438+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000fdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

```

Again this morning, even though the problem seemed fixed last night, I was thrown into an emergency shell instead of normal boot because of the problems with sdb1. I'll describe the problem as best I understand it.

I was writing a DVD .iso file to sdb1 when the computer lost all power, and just turned off. Subsequent attempts to switch it on failed with the power on button having no effect for a little while. One time I tried I noticed the fan on the CPU heatsink fire up a couple of revs before dying down.

I left it for a little while to reboot the computer, after which I am given the root emergency shell which tells me that a standard FSCK on /dev/sdb1 couldn't complete because the disk's UUID couldn't be recognized.

When I rebooted to see if it was a BIOS problem, trying to enter the BIOS normally gave me a disk recovery utility that I've actually never seen before. The options on there that I've tried so far (I'll find these out later) have failed.

Attempts to:
[INDENT]resolve the disk's UUID;[/INDENT]
[INDENT]FSCK the disk normally;[/INDENT]
[INDENT]e2fsck the disk specifying any number of backup superblocks;[/INDENT]
[INDENT]mount the disk[/INDENT]
All fail.

However, using testdisk I can see the disk, edit the partition's attributes (some of them, at least), and even browse some of the files that are on there.

The relevant part of my FSTAB:
> # /dev/hdd1
UUID=4b68e6b7-0ca8-4fc8-9af3-973c710846b0 /media/hdd1     ext3    defaults        0       2

But note that that UUID seems missing:
```
james@humDinger:~$ ls /dev/disk/by-uuid
6e5fcdb4-0716-44f4-ae88-899dbe87864d  9c92ab0d-ff43-4b62-a2e3-6261e9e652cb
7dd9afe9-08a4-4561-abc0-ad90ea1b9404
```

```
james@humDinger:~$ sudo vol_id -u /dev/sdb1
/dev/sdb1: error opening volume
```

How can I resolve this?

---

### Post by Jimmey on 2008-11-25
It is now (for the moment) working. 

Is there anything I should do now the disk seems okay that could maybe fix the problem?

---

### Post by Cracauer on 2008-11-25
Try a new power supply.

Seriously.

And only mount the filesystem in there readonly, your instable computer will scramble it's filesystems.

---

### Post by psusi on 2008-11-25
Yea, sounds like you have some serious hardware problems.  Maybe an insufficient power supply, or maybe an overheating cpu.

---

### Post by Jimmey on 2008-11-26
Yeah, I have reached that conclusion too.

The CPU seems fine because last I checked it was running relatively cool (54degrees).

I'm backing the PSU needs to be replaced - The current one is far too loud anyway. 

There goes another £50 of my hard earned cash on an unpredicted expense!

---

