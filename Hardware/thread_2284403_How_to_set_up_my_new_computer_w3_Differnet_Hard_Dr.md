---
title: "How to set up my new computer w/3 Differnet Hard Drives"
date: 2015-06-29
forum: Hardware
---

### Post by john409 on 2015-06-29
Hello!
I just ordered a new rig and was trying to figure out how to set it up.

When I placed my order, NewEgg threw in an extra SSD 120Gb so I will have:

Kingston SSDNow V300 Series SV300S37A/ SATA III     120GB
Corsair Force LX Series CSSD-F256GBLX/ SATA III      256GB
Seagate Barracuda ST1000DM003 7200 RPM 64MB Cache SATA 6.0Gb/s 1TB

I was just going to run programs from the 256 Gb and store data on the 1TB, but with the extra Kingston I need to rethink the plan. Should I be considering RAID? Or do I loose way to much storage? Or should I run UMBUTU from the 120 GB and programs from the 256 GB and storage on the 1 TB?

I want to get as much as I can out of my new system, but have no real experience with setting up from scratch like this.

Opinions??

---

### Post by dino99 on 2015-06-29
*****  Or should I run UMBUTU from the 120 GB and programs from the 256 GB and storage on the 1 TB? *********

This should be my own choice  ):P

---

### Post by john409 on 2015-06-29
But...what about data backups? Would a Raid system be useful?

---

### Post by weatherman2 on 2015-06-29
RAID mirror is useful to protect against drive failure.  But it does nothing to protect against accidental erasure or file system corruption.  RAID mirror doesn't replace a backup system.

I wouldn't RAID two SSD drives.  At best, I'd use one to backup the other one.

Unless you are an extreme power user, 256GB is far more than you need for software.  Even 120GB is probably adequate, if you have a huge hard drive for data.

I'd use one of the drives as a spare and leave it out.  I have found spare hard drives (or SSD drives) very useful for little projects: booting test operating systems, upgrading laptops, etc.  A 120GB SSD can give a huge boost to an old laptop if you find one.  Or, put it in a little USB enclosure and use it a little portable drive with various Linux distros on it - a work drive of sorts.

If you really want to use both SSDs in your system, you might look into setting up an LVM, which will let you combine two partitions on different drives into one logical volume.

---

### Post by john409 on 2015-06-29
I hadn't even considered not using the extra drive.

Would mirroring the small drive to the larger one create a backup that I could trust and boot from? Or do I run the risk of simply mirroring whatever corrupted my first drive into the second drive?

I have had a few HDD's go bad over the years, how often do SSD's go out? Or are they a bit more reliable because they dont have the moving parts?

---

### Post by weatherman2 on 2015-06-29
If you want to use that 2nd SSD as a backup, I'd make your root partition on the larger one only 120GB at most (so an exact copy will fit on the 120GB).  Then make a second partition on the larger SSD for the rest of the space - for whatever you want, I guess.  You'll still have the big hard drive for storage.  Really, 120GB is more than enough space for a Ubuntu root partition unless you are doing heavy code development.  I usually make mine only about 20GB or 30GB or so.

I highly recommend an LVM installation for a variety of reasons.  One is that LVM supports snapshots, meaning you can backup a live booted OS filesystem (something that can't be done reliably without a snapshot).  LVM is awesome - do some reading on it.  But, you could simply rsync your existing root partition (snapshot with LVM) to the other SSD with a partition of the same size.

But you could just make the backup to your big hard drive instead then restore the backup to the spare SSD if you need to.  There's no need to devote a whole separate SSD to having a backup of the other one, unless you don't really have room on the hard drive.  Spend some time learning how to make backups and restore them - you'll thank yourself later when you can do it in a stressful situation.  For example, learn to make an automated backup of your root partition to say the hard drive (in its own directory, not using the whole drive) then restoring it to the other SSD, then booting the other SSD successfully.  That's where having a spare "project" drive is really nice to have laying around.  I can't imagine not having one or two.

---

### Post by john409 on 2015-06-29
Thank you weatherman2 for the help. I will learn how to use LVM to make snapshots of my system onto my 1TB drive. 

How big of a partition should I make for the Ubuntu OS? I am a "novice" web developer, just finished college and am trying my hand at freelance work to get started. So I find myself installing various programs from the Ubuntu libraries like Gimp (which is awesome, once you figure it out). Do those installs land in my root?

---

### Post by weatherman2 on 2015-06-29
Yes, the installs land in your root partition (in /usr).  If you have the room, make it something like 50GB.  You can grow it or shrink it later if you want, and with LVM it's even easier to do.

---

### Post by weatherman2 on 2015-06-29
This intro to LVM is a few years old but should still apply.  Note that in 14.04 and newer versions of Ubuntu, LVM support should already be included so you need not install anything to use it:

[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

If you want to make a backup of your root filesystem which is installed on a logical volume in an LVM, here's how you might do it:

- create a snapshot of the logical volume
- mount the snapshot - say to some safe directory like /mnt/root-snapshot
- backup the snapshot, something like:

sudo rsync -a --delete -x /mnt/root-snapshot/ /mnt/hard-drive-data/root-backup/

- remove the snapshot

The snapshot tracks changes to the original filesystem since you created it - some space is need for this but not much.  If you have a 50GB root filesystem, maybe create a snapshot with 512MB or 1GB of space.  You won't keep the snapshot very long - just long enough to do the backup - then remove it and re-create it again next time.  Otherwise, it will fill up as the filesystem changes.

(If you don't know what rsync is - learn it, it's incredibly awesome.)

If someday you need to restore your backup, you could do it with another rsync and a live USB boot.  If you are restoring to a different disk, you can create new partitions and install Grub on the new disk (and maybe edit your /etc/fstab to pick up changes) and that should be all you need.

---

