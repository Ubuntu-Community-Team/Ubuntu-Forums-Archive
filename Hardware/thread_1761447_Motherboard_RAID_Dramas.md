---
title: "Motherboard RAID Dramas"
date: 2011-05-18
forum: Hardware
---

### Post by Abaddon on 2011-05-18
Hi all,

I've recently built a new computer which I'm dual booting Win7 (for games) and Natty (for everything else).  After some drama, I managed to get everything installed, but I'm having some dramas with the RAID setup.

I have a SSD, partitioned for Win 7, Ubuntu and Home.  No probs.
I also have 2x 2TB HDDs which the plan was to have in a RAID1 from the RAID controller on my harddrive. They are partitioned into 2x ~1Tb partitions - one formatted NTFS for games in Windows and the other as a shared data partition.  It is currently formatted NTFS because I formatted it in Windows, but I'm not fussed about the filesystem - although a windows-friendly system would be preferable so I can share between Win/Natty without stuffing around.

Win7 recognises the RAID no problems.

I got Natty to recognise them no worries with ntfs-config, but the first time I rebooted, there was an error message during the splash loader about not being able to mount the drives.  I skipped mounting them and reverted to the old fstab - but now I can't seem to get natty to recognise them at all.

I've attached a screenshot from GParted.

Also:

```
blkid

/dev/sda1: UUID="AAD03FA0D03F71A5" TYPE="ntfs" 
/dev/sda5: LABEL="ubuntu" UUID="8ffac6e9-7dc2-4282-ad6f-59185183b455" TYPE="ext4" 
/dev/sda6: LABEL="home" UUID="a9c59734-53c6-4c93-9189-6e0ad46a1c62" TYPE="ext4" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd1: LABEL="My Passport" UUID="682A-0050" TYPE="vfat" 
```

(My Passport is an external drive I've got plugged in)

```
fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=8ffac6e9-7dc2-4282-ad6f-59185183b455	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=a9c59734-53c6-4c93-9189-6e0ad46a1c62	/home	ext4	defaults	0	2
#Entry for /dev/sdi1 :
UUID=F21843B31843759F	/media/archive	ntfs-3g	defaults,nosuid,nodev,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=AAD03FA0D03F71A5	/media/windows	ntfs-3g	defaults,nosuid,nodev,locale=en_AU.UTF-8	0	0

```

Also, this appears in the terminal if I run gparted from the terminal prompt:

```

======================
libparted : 2.3
======================
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/mapper/isw_bgeiebgiac_RAID appears to be used, you can fix the GPT to use all of the space (an extra 264 blocks) or continue with the current setting? 
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 6320 blocks) or continue with the current setting? 
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Not all of the space available to /dev/sdc appears to be used, you can fix the GPT to use all of the space (an extra 6320 blocks) or continue with the current setting? 

```

Where has my RAID-y goodness gone?

Thanks in advance.

---

### Post by Abaddon on 2011-05-22
apologies for the bump, but I'd like to try and get this sorted out without having to do a reformat!

---

