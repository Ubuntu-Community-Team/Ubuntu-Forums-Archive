---
title: "Karmic. 4 drives. 2 corrupt. Why?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2009-10-29
I have 4 drives in my system. 3 are backups I mount in fstab, while I work off of the main one.

During the install, I was just dealing with my main 2 drives, which are 500gb. They responded fine. I left the other 2 drives untouched and did not format them.

I booted up for the first time and bam there was my main backup drive (the 2nd 500gb drive) but my pair of 250gb drives (drive 3 and 4) did not want to mount when I issued a mount command.

sudo fdisk -l + sudo blkid


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       60801   406460565    5  Extended
/dev/sda5           10200       10321      979933+  82  Linux swap / Solaris
/dev/sda6           10322       13360    24410736   83  Linux
/dev/sda7           13361       60801   381069801   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007269c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30515   245111706   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43e0877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   83  Linux
jason@Area51:~$ sudo blkid
/dev/sda1: UUID="78461C2D41973A21" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="eacce669-8150-428b-9ac9-fe04025b027b" TYPE="swap" 
/dev/sda6: UUID="170daa2f-6dfb-4ac4-8bb2-5b8a2ebf3caa" TYPE="ext4" 
/dev/sda7: UUID="1499253e-2cc8-4201-81ad-faae2906ac33" TYPE="ext4" 
/dev/sdb1: UUID="b2354e40-cd24-41eb-b41b-0aadc9933166" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc: TYPE="nvidia_raid_member" 
/dev/sdd: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_dgcbcfbj1: UUID="772764b7-e571-4897-ba6d-ded412a5e814" SEC_TYPE="ext2" TYPE="ext3" 
jason@Area51:~$ 


What's with nvidia raid member? These aren't raid disks. They're simply mounted so I can rsync data to them.

---

### Post by Roasted on 2009-10-29
Okay. I'm pissed. I'm very pissed.

So I was in IRC and some guy suggested that Ubuntu is trying to play smart and assumes that because the drives are identical that they're RAID.

I unplug one 250 and boot up with 500/500/250. Okay, great. The single 250 was fine. SO I thought hey okay we'll add that 250 to fstab, then reboot, and power on the last drive, and the other 250 would respond accordingly since the original 250 would already be in fstab.

Now I'm getting

Could not update ICEauthority file /home/jason/.ICEauthority.

So I found a tutorial from last year on how to fix it from the root shell, oh, the file doesn't exist.

What the ****?

EDIT - I'm in the root shell now. It seems as if no home directories exist. Awesome.

EDIT - It seems as if I'm an idiot. I messed up fstab and was mounting my home directory on a different drive. Anyway, how do I fix the raid thing? I CANNOT have karmic thinking those disks are raid...

---

### Post by Roasted on 2009-10-30
Need my system running ASAP...

Why does Karmic look at these drives as RAID?
How can I prevent Karmic from looking at these drives as RAID and just hook them up with fstab like any normal distro?

EDIT - Now I'm having an issue with fstab... tell me, what's wrong with my fstab??

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=fce120c6-93ce-4541-b0c6-c9df534c3235 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=1499253e-2cc8-4201-81ad-faae2906ac33 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=eacce669-8150-428b-9ac9-fe04025b027b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#
#
#BACKUP DRIVES
# /media/localbackup was on /dev/sdb1 during installation
UUID=b2354e40-cd24-41eb-b41b-0aadc9933166 /media/localbackup ext3    defaults        0       2
#
# /media/storage
UUID=772764b7-e571-4897-ba6d-ded412a5e814 /media/storage ext3    defaults        0       2

I have the proper UUID's for storage and localbackup accordingly. When I boot up and select places - drive, I get Error mounting: mount exited with exit code 1: helper failed with mount: only root can mount /dev/sdc1 on /media/localbackup.

I thought that was the point of fstab? To like, mount the drives automatically with root?

---

