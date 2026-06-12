---
title: "partitions with gparted versus Ubuntu Live CD"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by sanford55 on 2009-08-18
Hi everyone.  I have installed Ubuntu to dual boot with XP on several machines.  I used the Ubuntu Live CD to create my Linux partitions during the install.  But while researching the creation of a separate shared data partition, I noticed that lots of folk recommend beginning by partitioning with Gparted to create the partitions (root, data and then swap) and only then installing Ubuntu.  Is there some advantage to doing it this way rather than letting the Ubuntu live CD do all the work?  Will the Ubuntu live CD understand that it should put Ubuntu in the right place and take the other partitions as swap and data?  Since I specify in gparted that one partition is Ext3 and the other is swap, I suppose the installation disk should figure that out, but what about the NTFS or Fat32 data partition?  Do I have to tell it after the install that it should use the data partition?  How?  I am installing Ubuntu to dual boot with XP on a friends machine and do not want to screw this up! (By the way, has anyone else noticed that the spell checker for the Ubuntu forums does not recognize the word "Ubuntu"!)  Thanks for any help.  Sanford

---

### Post by raymondh on 2009-08-18
> **sanford55 said:**
> Hi everyone.  I have installed Ubuntu to dual boot with XP on several machines.  I used the Ubuntu Live CD to create my Linux partitions during the install.  But while researching the creation of a separate shared data partition, I noticed that lots of folk recommend beginning by partitioning with Gparted to create the partitions (root, data and then swap) and only then installing Ubuntu.  Is there some advantage to doing it this way rather than letting the Ubuntu live CD do all the work?  Will the Ubuntu live CD understand that it should put Ubuntu in the right place and take the other partitions as swap and data?  Since I specify in gparted that one partition is Ext3 and the other is swap, I suppose the installation disk should figure that out, but what about the NTFS or Fat32 data partition?  Do I have to tell it after the install that it should use the data partition?  How?  I am installing Ubuntu to dual boot with XP on a friends machine and do not want to screw this up! (By the way, has anyone else noticed that the spell checker for the Ubuntu forums does not recognize the word "Ubuntu"!)  Thanks for any help.  Sanford

It could be done either way .... choosing manual during the partitioning stage.  

Some folks prefer to create the partitions beforehand, as you mentioned. They probably do that as their HD set-up may be complicated, etc.  I do because I use a standalone gparted disk instead of the going to the liveCD and in live session. And when it comes time to install, I just select manual > edit > set to 'use' > the respective mountpoints > and if needed, the file format.

Again, you can partition prior, or during the actual, installation.... with no outright advantage except for user convenience and current skill.

As for the /data partition, Ubuntu ought to mount it automatically (see places and rt. click on the partition.  Otherwise, manually mounting it can also be done.... as you very well know.

Back up files.

---

### Post by Mark Phelps on 2009-08-18
> **sanford55 said:**
> ... Is there some advantage to doing it this way rather than letting the Ubuntu live CD do all the work? 
They are the same program. In terms of partitioning, they provide the same capabilities.
>  Will the Ubuntu live CD understand that it should put Ubuntu in the right place and take the other partitions as swap and data? 
Yes
>  ... but what about the NTFS or Fat32 data partition?  Do I have to tell it after the install that it should use the data partition?  How?  
You can't install to NTFS or Fat32 volumes; you will need to install to Ext3 or Ext4 volumes. But after install, you can access your NTFS and FAT 32 volumes through "Places" or you can choose to automount them by adding info to your /etc/fstab file

Personally ... I prefer to use the GParted LiveCD to pre-partition the drive because (1) the gparted version on their LiveCD tends to be more current than the one bundled with Ubuntu, (2) since I have several disks and lots of partitions, this helps prevent me accidentally overwriting the wrong partitions during the installation, (3) gives me a chance to check the partitions after formatting to ensure I did the right thing before proceeding with the installation.

---

### Post by theozzlives on 2009-08-18
You can install to any linux file system:
1. root (/) about 10 GB
2. /swap twice your memory
3. /home (what you want to save your settings, and other users' documents & settings)
4. You can make an NTFS for data, (I haven't tried this except for /root but you can probably make a mount point of /data or /home/data, NTFS, by typing it in).

You want to do a Manual partitioning during the install to obtain these goals.

---

