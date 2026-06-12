---
title: "How to remove an MDADM Raid 1 Array"
date: 2008-08-26
forum: General Help
---

### Post by marke1 on 2008-08-26
Hi, we've got a server using mdadm for a RAID 1 array (mirrored set). We want to remove the RAID - and this is on a remote server so we don't have physical access to the system, but we do have root shell access. 

I read the info in this thread: 
[http://ubuntuforums.org/showpost.php?p=2459683&postcount=2](http://ubuntuforums.org/showpost.php?p=2459683&postcount=2)

Which basically says to remove the array do this: 

> 
1. sudo fdisk -l

2. Query your arrays to find out what disks are contained using
Code:

sudo mdadm --detail /dev/md0
 (or md1 or whatever)

3. Shut down the array using
Code:

sudo mdadm --stop /dev/md0

4. Unmount the file system

5. Zero the superblock FOR EACH drive
Code:

sudo mdadm --zero-superblock /dev/sda (or hda)
sudo mdadm --zero-superblock /dev/sdX...


So my question is: Can I do all that using a remote SSH shell without getting disconnected (other than because of typical connection problems), and if I do that will the operating system still boot? Or do I have to completely reinstall everything? 

Any help or advice will be greatly appreciated!

---

### Post by cariboo on 2008-08-26
Are you using your array for everything or just for data, It really depends how you have your system set up and where the mbr is.

Jim

---

### Post by marke1 on 2008-08-26
> **cariboo907 said:**
> Are you using your array for everything or just for data, It really depends how you have your system set up and where the mbr is.

Jim

The system has only two disks (mirrored via RAID 1). The OS and all data (Web files, MySQL databases, mail, etc) are stored on the primary disk, which is of course mirrored on the secondary disk.

---

### Post by fjgaude on 2008-08-26
Can you backup your important data? and then start over? If the OS is on this raid1 array I'm not sure how to get rid of the array without first dropping one drive, making sure the grub remains on the drive remaining.

Do you know if grub in on both drives?

---

### Post by marke1 on 2008-08-26
> **fjgaude said:**
> Can you backup your important data? and then start over?

Sure. But I don't want to do that. It's a lot of work though - lots of apps to install and all sorts of config to do, even with backups. So if I can avoid a reinstall then that's what I want to do. 

> Do you know if grub in on both drives?

Not sure. What I do know is that one drive is a mirror of the other and I don't know what all gets mirrored. Taken literally I'd assume everything gets mirrored. 

So I figure if I drop the IDE slave drive from the array (force it into fail mode so that MDADM thinks it's bad) then that'd be Ok. Then maybe I can unmount it and zero out the superblock to get rid of the RAID signature on the drive. That would probably work Ok. But, that still leaves the primary drive with a RAID signature on it. So I'd need to get rid of that signature by zeroing the superblock on that one too. 

I guess what I need to know is what happens if I zero a superblock on a drive? Does that make it non-bootable or mess up the boot loader in any way?

---

### Post by fjgaude on 2008-08-27
> I guess what I need to know is what happens if I zero a superblock on a drive? Does that make it non-bootable or mess up the boot loader in any way?

I can't say because I've never had a need to do such a thing. I've not read of anyone else doing it.

My guess is that the superblocks are only associated with software raid, so zeroing them out should leave everything else alone. But as I've said, I've never had a need. And right now I'm not in a position to test it for you.

A mirror doesn't mean that the MBR is copied... thus we don't know about the **grub**.

---

