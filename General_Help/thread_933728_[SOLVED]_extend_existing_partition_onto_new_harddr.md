---
title: "[SOLVED] extend existing partition onto new harddrive?"
date: 2008-09-29
forum: General Help
---

### Post by gschoppe on 2008-09-29
I just bought a second 500GB HDD for my media server, and am looking to add it in without upsetting my current file structure... my current partitions are:

OS   - 40gb ext3
Data - 410GB (or so) ext3

is there a way to extend the Data partition to include the new drive... as with RAID, but without formatting?

---

### Post by Rocket2DMn on 2008-09-29
No, the only way to do this is to use LVM (logical volume manager) which has the capability to do RAID.  Basically, you can't have "partitions" across physical devices without using LVM.  I suggest just formatting the new drive with the file system of your choice and adding the appropriate entry to fstab.

---

### Post by gschoppe on 2008-09-29
could I use LVM to RAID the drives without formatting?  I know it can resize partitions...

---

### Post by Rocket2DMn on 2008-09-29
To my knowledge, no.  The file systems on the disks have to be setup with LVM, and I believe the entirety of each disk needs to fall under the volume group.  AFAIK, you can't use one and a half harddrives with LVM - it's all or nothing (though you can use drives in LVM alongside other drives NOT in LVM, but it gets complicated and can cause pain in booting the system).

---

### Post by shaggy999 on 2008-09-29
I don't think that's true because when I set up encryption on my hard drive I partition the hard drive into 2 partitions: a /boot partition (which is unencrypted) and a second partition which I set up as an encrypted layer. On top of that encrypted partition I set up lvm and then split the lvm into /home, /, and a swap. If lvm requires an entire drive then I shouldn't be able to do that.

The trick here, though, is that I do believe that if you set up RAID then each volume for RAID must be the same size. This would mean if you've got 410 GB of space for lvm on one drive then you'd have to split the second drive into 410GB + extra as well and the raid would be the combination of the two 410 GB partitions. This means you're wasting space, basically.

---

### Post by Rocket2DMn on 2008-09-29
Upon further inspection of a CentOS install using LVM, it seems you may be right.  A separate /boot partition is definitely necessary when you are using an encrypted partition since you can't read it until the boot process starts and has the ability to decrypt.  You may be able to get a VolGroup to exist on part of a hard drive and cover a complete other drive, as far as the OP's question, the area to be placed inside the LVM would still have to be formatted first.  Setting up a LVM is changing the filesystem as it is changing the device.
```
[root@localhost ~]# fdisk -l

Disk /dev/hda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
**/dev/hda2              14        1044     8281507+  8e  Linux LVM**
[root@localhost ~]# mount
**/dev/mapper/VolGroup00-LogVol00 on / type ext3 (rw)**
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hda1 on /boot type ext3 (rw)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
```
Above you can see the filesystem and device location.

For the OP, if you *were* to be able to set this up without reformatting the partition, you would most likely be stuck with a striped array (RAID-0) in which there would be no backup, so if one drive failed, you would lose all the data (unlike in a RAID-1 setup which mirrors the storage).  However, I don't believe it is possible to do the setup without formatting first.

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by gschoppe on 2008-09-29
I'm sorry, I didn't mean RAID-1 mirrored, but rather RAID-0 striped... it was a typo... I'm just looking for a way to span two HDDs to make one larger logical drive, but I think I need to have a drive that I can backup my data to for the process to work...

I don't need parity, as nothing is mission critical

---

### Post by Rocket2DMn on 2008-09-29
Ok, I understood your original request, about having the partition span two hard drive - that is what LVM can be used for, but I believe you would have to reformat the partition you want to extend into the second drive (thus creating a logical volume).  If you just want to use the drive for backup, I would do what I suggested in my first response, which is to just format the new drive with your filesystem of choice (probably ext3), then add it to fstab (and create the mount point, etc).  Then you can use backup software or manual backups to backup your data to the second drive.  This would be similar to using an external disk (except no unplugging and needing to mount on the fly).

Perhaps you don't know what I'm talking about?  fstab, located at /etc/fstab stores mount locations for different static storage devices on the system (so dynamically added storage like USB flash drives do not have entries here).  I can help you set this up if you would like.

---

### Post by gschoppe on 2008-09-29
I understand fstab, but I'm in an uncommon situation... basically, my Ubuntu box is only used as a webserver, and to host all of my media files... It presents a SAMBA share to all the other computers in my network, with subfolders such as movies, tv, music, files, and programs.

I was hoping to add space to this shared drive without having to have two shares, as having two of each category folder (one on each drive) gets confusing.

 I also have automated recording and ripping scripts running that I use to catalog and store data, and I don't want to make them work with two drives...  

I may need to rethink how to do this...


could I perform the following sequence to get the result I need:

1) resize my current media partition down slightly to create a lkittle bit of unallocated space on drive 1 (the current drive)

2) use LVM to create a logical volume that spans the unallocated space on drive 1 with all the space on drive 2.

3) copy my data from my media partition to this new spanned partition.

4) delete my media partition

5) resize the spanned partition to fill the newly unallocated space on drive 1

6) set the new spanned volume to the same mount point the old partition used.

7) PROFIT!!


is that a possibility?

---

### Post by Rocket2DMn on 2008-09-29
Theoretically, it seems like it should work, however, I've never tried resizing logical volumes - I don't know if programs like GParted will do this on a LVM (though I expect they should).  I'm always a bit hesitant to resize partitions because if something goes wrong, you can screw yourself pretty hard.  However unlikely, if something were to go wrong during your process, you would lose everything, and I wouldn't be doing my job by just telling you to do this without letting you know of the risks involved.

**A Much Safer Alternative**
It should be possible to just format the drive like I said, then set the mount point to be under directory structure of your current share.  As long as the permissions in that subtree match the permissions of the share, you should be able to access everything on the new drive.  I have tested this on my network with samba.  Since I don't have it fully configured, I just dropped the firewall on the host and was able to access the flash drive I used in full through the existing samba share (but since you already have your firewall configured, it shouldn't be an issue).
Example:
Samba share at ~/testshare
Mount new drive at ~/testshare/mount

I need to head out now, I'll check on you tomorrow evening.  Good luck.

---

### Post by gschoppe on 2008-10-01
I used the LVM Method, but I may have a problem... I have had my home partition the same as my media partition... it appears this means I cannot unmount it while logged in, and therefore cannot expand the LV I created to fill its Volume Group...

I am going to move /home to a new LV, and make my media a partition that mounts to /home/shared... I think this will make things easier for the future.

---

### Post by gschoppe on 2008-10-01
NEW ISSUE - i just added a new LV, mounted at /newhome ... I copied /home to /newhome  and restarted into recovery mode.

I opened fstab with vi and swapped mount points between /newhome and /home ... 


now my system is going to recovery at boot, saying

fsck failed

fsck:ext3 unable to resolve UUID: *(the UUID)*

or something similar...

any idea what I did?

I even went back and reswapped mount points in fstab, to no avail... help?

---

### Post by Rocket2DMn on 2008-10-01
You will need to boot from a LiveCD in order to unmount /home and resize it.  As always, make a backup first.  I usually suggest the GParted LiveCD - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) - it should be capable of working with LVMs.

---

### Post by Rocket2DMn on 2008-10-01
> **gschoppe said:**
> NEW ISSUE - i just added a new LV, mounted at /newhome ... I copied /home to /newhome  and restarted into recovery mode.

I opened fstab with vi and swapped mount points between /newhome and /home ... 


now my system is going to recovery at boot, saying

fsck failed

fsck:ext3 unable to resolve UUID: *(the UUID)*

or something similar...

any idea what I did?

I even went back and reswapped mount points in fstab, to no avail... help?

Yes, when you changed the partitions, the UUID changed, and that is what /etc/fstab uses to recognize partitions.  You can update it by using the correct UUID as seen with
```
sudo blkid
```
(no sudo in recovery mode)
UUIDs are replacing /dev locations for statically mounted devices, but it is still possible to use /dev locations if you prefer.

---

### Post by gschoppe on 2008-10-01
Thank you, everything is working fine now... my fstab had an extraneous entry that was causing issues...

once again: THANKS!!

---

