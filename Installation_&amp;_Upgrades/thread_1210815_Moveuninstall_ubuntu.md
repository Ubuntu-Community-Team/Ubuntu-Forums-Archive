---
title: "Move/uninstall ubuntu?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Khrimzunn on 2009-07-11
I want to keep ubuntu, but not on the current HDD. How can I make ubuntu keep my settings, but be on a seperate HDD? I have a 500G internal drive that I'm sharing between vista and ubuntu. I want vista to have the entire HDD dedicated to itself and ubuntu to have a new HDD dedicated to it. So how would I go about doing that? I don't want to uninstall ubuntu and reinstall ont eh new drive because I want to keep my current settings as they are. 
I'm not sure if it's clear enough, I'm a bit tired and out of it atm.

---

### Post by Herman on 2009-07-12
You'll need to know the partition number of your current Ubuntu partition. Check with a partition editor like GParted, or run the 'sudo fdisk -lu' 'sudo blkid' command(s) to check.

You'll need to know the partition number you want to copy it to.

You'll need to make sure the partition you want to move is equal or smaller than the partition you have ready in the other hard disk that you want to copy it to.
If it isn't you might need to shrink your Ubuntu partition first.
```
dd if=/dev/sda2 of=/dev/sdb1 bs=4096 conv=notrunc,noerror
```Where: '/dev/sda2' is your Ubuntu partition
Where: '/dev/sdb1' is the empty partition in your other hard disk where you want to copy Ubuntu to.
[COLOR=Red]CAUTION: Be very careful with the dd command, if you run it backwards and copy an empty partition to a partition with data in it, you'll lose your data unless you have it properly backed up. Probably you should back up your data first.[/COLOR]

You'll need to re-install GRUB and delete the old Ubuntu partition and that should be about it.

Regards, Herman :)

---

### Post by Herman on 2009-07-12
I almost forgot one thing, you might want to boot your Ubuntu Live CD and run resize2fs to make sure the file system is grown to fill the new (larger) partition,
```
resize2fs -p /dev/sdb1 
```
Or, just right-click on it in GParted and run a file system check on it with GParted, that will also resize the file system right after the file system check.

---

### Post by Khrimzunn on 2009-07-12
But what if I want ubuntu to use the whole disk? And grub I think I can figure out how to fix it. The other issue is windows recognizing that I gave it back it's original HDD space.
EDIT: Whoops misread a line. I'll get to it.
EDIT:
I can't get it to work.
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb2 of=/dev/sda bs=4096 conv=notrunc,noerror
0+1 records in
0+1 records out
1024 bytes (1.0 kB) copied, 0.00693251 s, 148 kB/s
```

---

### Post by Herman on 2009-07-12
After you copy Ubuntu to the new partition in the other hard disk, you can use a partition editor to delete the old copy of Ubuntu from the hard disk you have Windows in.
Then you can click on your Windows partition and resize it to fill the disk, over the empty space where Ubuntu used to be.

In you new hard disk, which has Ubuntu in it , if you want to make the partition larger, just resize it if there's room.

A good partition editor to use would be GParted in your Ubuntu Live CD, (Gnome Partition Editor), because you probably already have a Ubuntu Live CD. 

If you want a dedicated partition editing CD with the latest up to the minute software in it you can use [Parted Magic]("http://partedmagic.com/") Live CD or a [GParted -- LiveCD]("http://gparted.sourceforge.net/"). Either of those are only a small download, and contain some other very handy related software which you might find useful someday. 

Windows Vista has the unusual habit of making the first sector of it's partition in sector number 2048, instead of sector 63 like every other operating system.
Just make sure you remove the checkmark from the 'round to cylinders' checkbox before touching any Windows 7 or Vista partitions with a partition editor. If you accidentally move the boot sector of a Vista/Win 7 partition it may make the operating system unbootable and it may require a little additional work to be able to boot Vista/Win 7 again.
If you do accidentally move ****the start of a Windows Vista or Windows 7 partition for some reason, you can fix the problem of not being able to boot anymore merely by booting from your Vista CD and choosing 'repair Computer', ****and the CD will reconfigure the Vista Boot loader for you.
If it doesn't work, go to the command prompt and run BOOTREC /FIXBOOT.
That should fix it.

You'll also probably notice Windows doing a CHKDSK (file system check) after resizing with GParted. That's because GParted tells it to by placing the 'dirty' flag in the file system to induce Windows to run a file system check, it's perfectly normal and recommended. It's important to let the file system check complete inunterrupted, it will only take a few minutes.

You can use Windows Vista's own partition editor instead for resizing Vista if you prefer. It's a bit basic but it'll do the job. It should be in your Vista CD.




****

---

### Post by Khrimzunn on 2009-07-12
I can't move the ubuntu partition witht he command you gave me. I replaced what was needed witht he correct info. Problem is it's not copying it. Also, what file system should the new disk be? Right now it's "unallocated".

---

### Post by Herman on 2009-07-12
What's the output from 'sudo fdisk -lu'?
```
sudo fdisk -lu
```

---

### Post by Khrimzunn on 2009-07-12
Can't check now, I'm copying the ubuntu partition. The problem looks like it's the issue about copying swap as well as the linux partition. Looks like it's working now if I copy one by one. I'm not sure why it didn't let me copy swap.
EDIT I opened a new terminal session.
```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000472ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d445d44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   752323949   376160951    7  HPFS/NTFS
/dev/sdb2       752323950   976768064   112222057+   5  Extended
/dev/sdb5       752324013   967562819   107619403+  83  Linux
/dev/sdb6       967562883   976768064     4602591   82  Linux swap / Solaris

```

---

### Post by Herman on 2009-07-12
:) Okay, as long s it's working okay now.

I'll show you what you did wrong just for the future,
```
sudo dd if=/dev/sdb2 of=/dev/**[COLOR=Red]sda[/COLOR]** bs=4096 conv=notrunc,noerror
``` Should have been,
```
sudo dd if=/dev/sdb2 of=/dev/**sda1** bs=4096 conv=notrunc,noerror
```You can copy a partition to another partition, but you can't copy a partition to a MBR, or to a whole disk. You can copy a whole disk to a whole disk though. :)

Probably the swap area doesn't matter, I wouldn't lose any sleep over that, just make a new swap area with a partition editor. Or copy it if you want, doesn't matter.

---

### Post by Khrimzunn on 2009-07-12
I just made a swap and now I'm recopying it all over again. I feel stupid now lols. So the grub how would I fix it to recognize that it's been moved? Run these commands?
```
sudo su
```
```
grub-install /dev/sda2
```

Or do I need to do some funny and ugly things?

---

### Post by Herman on 2009-07-12
Here, try this link, [Re-install GRUB with a GRUB shell]("http://members.iinet.net.au/%7Eherman546/p15.html#Re-install_Grub_with_Live_CD").I gotta go to work, it's Monday morning where I am and I'm almost running late already, back later, bye for now and good luck, C ya! ):P

---

### Post by Khrimzunn on 2009-07-12
Ok, thanks for the help.

---

