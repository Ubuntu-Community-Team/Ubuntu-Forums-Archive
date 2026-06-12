---
title: "Formatting a 4TB HDD for mass storage"
date: 2013-03-31
forum: Hardware
---

### Post by Smittysmit on 2013-03-31
I have a Seagate 4TB drive that I want to use strictly for video archive but can't get it formatted.  I have read a few threads/sites and it points go gdisk but can only get 1.7TB.  Is there an easy way to see all 4TB?  I'm not the best at terminal but can copy/paste just fine.

I am using Ultimate Edition 3.4 in 64-bit.  I do have access at work to a Win-7 & Win-8 machine if that simplifies things but would be connected via Thermaltake USB dock.

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by Smittysmit on 2013-03-31
Think I found the problem but another issue.  I had on the USB 'SATA dock' and tried Gparted in the beginning.  Finally connected it straight to the SATA bus and Gparted found it with table errors.  Let it fix it and created a new partition in ext3.  Rebooted and didnt find it.

What file system should I format this based on only using as an archive drive that will only be powered occasionally.

---

### Post by oldfred on 2013-03-31
Unless you have Windows handy, I would not use NTFS, as when you have to run chkdsk it will take forever. Since video you may want one large partition, but I normally prefer smaller partitions so fsck can run on one partition. File corruption may occur primarily power failure and then you have to run fsck for ext3 or ext4 formats.

Some have posted issues with some USB caddies with very large drives not being seen correctly. 

gdisk should have worked as well as gparted.
For gparted - 
 Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

---

### Post by Smittysmit on 2013-03-31
In Gparted, went advanced & choose gpt.  It still shone as 'unallocated'.  I assume that I now need to create a new partition.  What is the FS of choice?

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by Smittysmit on 2013-03-31
Formatted in ext4.  Transferred several files and all looked fine.  Unmounted drive and rebooted.  System booted  and powered on "hot-swap" SATA drive but doesnt see drive.  The HDD light has been on for over 30 minutes but wont see this drive.  Gparted doesnt see it either.

---

### Post by oldfred on 2013-03-31
As an internal drive or from caddie? IF caddie, then I might suspect it does not support large drives.

---

### Post by Rsxhawk on 2013-05-16
I am also trying to format a large 4TB drive I pulled out of an external enclosure and hooked up inside my Ubuntu PC, its a Seagate Backup Plus if that matters.  I can use disk utility to format the drive in EXT4, but as others have said above, I cannot partition it via msdos MBR due to limitations.  So that leaves me with a formatted EXT4 drive with a folder in it called Lost and Found of which I have no permission to open or even delete.  I tried using Gparted at this point to create a new partition table and that seemed to work, however when I attempt to actually create the ext4 partition on the new GPT partition table, it errors out on the mkfs command and just fails.

---

### Post by oldfred on 2013-05-16
I have BIOS but use gpt on smaller drives. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

Or you can use gdisk.
sudo apt-get install gdisk

      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

If not familar with ownership & permissions you have to set those and mount partitions with fstab.
Good example here:

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

More info:
      
 [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Rsxhawk on 2013-05-19
Will using the drive without a partition table be harmful or are there  disadvantages I should know about?  The drive seems to be working just  fine without a partition table, but I was just curious.  I haven't tried  gdisk yet, but I may keep that in mind for a rainy day.  The disk I'm  using houses all the tv shows and movies from my plex server so I can  stream them over to my ps3 over my home network.  it would be a bit of a  pain to transfer the data off and back on again.

---

### Post by oldfred on 2013-05-19
A lot of tools do not work without partition tables. Several have posted once they unmount & try to remount drive it does not as they just formatted it, without partitions.
Not sure how you even format without partitions as that would then be more like a huge floppy drive and not a partitioned hard drive?

---

### Post by Rsxhawk on 2013-05-19
Ha ha, yea I see what you're saying.  What I did was go into disk utility and choose "format drive" and chose "don't partition" since I was having MBR and GPT partition table creation failures.  Then within that same utility I chose ""format volume" and chose EXT4 and was almost set.  The only other thing I had to do was edit /etc/fstab and make sure the entry for the drive (in this case, sdc) read out as /dev/sdc instead of /dev/sdc1, where the "1" would have been the partition.  I made sure to change the setting to "auto" so it mounts at startup and it appears to be working just fine.

---

### Post by Rsxhawk on 2013-05-19
Also, Gparted still shows the disk as sdc1, but I couldn't get it to work until I edited fstab to use "sdc" instead of "sdc1".

---

