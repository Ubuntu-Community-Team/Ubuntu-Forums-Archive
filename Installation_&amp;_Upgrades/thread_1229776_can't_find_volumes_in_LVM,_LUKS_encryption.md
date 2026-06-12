---
title: "can't find volumes in LVM, LUKS encryption"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by touchlikefire on 2009-08-02
My last question before I sadly reformat the entire drive is a volume manager one. How can I get my volumes back? I rewrote the partition table with identically sized partitions, but did NOT format any partitions. So, the data is still there and intact, I just need to make the volume manager 'see' the volumes.

In chronological order, this is what happened:

   1. I booted alternate cd
   2. not knowing that I had to go to RECOVERY MODE, i proceeded with the installation of Jaunty
   3. I went through the partition creation, making sure i did NOT format the partitions
   4. then it asked about volumes, so I attempted to create them
   5. after realizing this might hose my system, i canceled the whole operation
   6. I booted into the LiveCD, verified that my hdd appeared unformatted and empty
   7. tried to resurrect my volumes via volume manager, but no dice


Not to belabor the pt, but to be clear: I created a new, identically sized (LUKS encrypted, same passphrase) partition via the Jaunty installer, and now my volumes are gone. Can I get them back?

---

### Post by unutbu on 2009-08-02
Have you tried something like this: [http://ubuntuforums.org/showpost.php?p=7399077&postcount=13](http://ubuntuforums.org/showpost.php?p=7399077&postcount=13) ?

---

### Post by touchlikefire on 2009-08-13
thx for the link. I went through the steps, but when i get to ```
vgchange -ay
``` the response is: ```
0 logical volumes in volume group "VolGroup00" now active
```

so...now what?

is it possible that my original volume group has been over written? If so, am I hosed?

---

### Post by unutbu on 2009-08-13
Well, I wouldn't put anything beyond the realm of possibilty (because I don't know enough about how LUKS+LVM work and I don't know how much has been overwritten), but if there is a way to restore your system, I'm afraid it requires more magic than I know.
I am sorry.

---

### Post by touchlikefire on 2009-08-13
Thanks for the help. None of the data should have been overwritten, aside from the partition table. Is there a way to search deeper for backup or overwritten LVMs?

---

### Post by unutbu on 2009-08-13
Well, if only the partition table has been modified, then there is a program called testdisk which can search for old partition table entries, and restore them. Although testdisk is an Ubuntu package in the repository, it wouldn't hurt to try the latest version. Here is how:
```

cd ~/Desktop
wget http://www.cgsecurity.org/ testdisk-6.11.3.linux26.tar.bz2
tar xvjf testdisk*.tar.bz2
sudo testdisk-6.11.3/linux/testdisk_static
```

Select "No Log", "Proceed", "Intel", "Analyse", "Quick Search", "Deeper Search"
The Deeper Search may take some time.
Use the up/down arrows to move among your partitions.
Usually you would press 'p' to try to list files inside the partitions. Since yours is LUKS encrypted, I doubt you'll be able to see anything useful, but perhaps you will be able to guess which one is your old partition.

Use the left/right arrow to change the partition type from "D" (for Delete) to "P" (for primary partition). (I assume your LUKS+LVM is for your entire hard drive except for the boot partition, so it would be a primary partition.)

Then write the new partition table to disk, and quit.

Good luck.

---

### Post by touchlikefire on 2009-08-14
Good idea! I'm acquainted with testdisk as I've used it a number of times in the past.  I ran a quick scan, per your suggestion, and got a number of funny results.

First, it said that /dev/crypt (as I'll call the encrypted drive) didn't have the end sector 0x00AA or something similar.  Then, it took nearly 8 hours to quick scan, where upon it said I had close to a million TB of diskspace - clearly inaccurate.  It said showed a number of questionable deleted partitions in the table:
```
Disk /dev/mapper/nvidia_effcehjh - 640 GB / 596 GiB - CHS 1250284800 1 1
     Partition               Start        End    Size in sectors
D Linux                         63       2118       2056
D FAT12                   24166551   24187289      20739 [NO NAME]
D Linux Swap              30561952   30562191        240
D FAT12                   35023344   35026223       2880
D HFS                     65765301 1029972105  964206805 [A^B UQ^A hQ^AOpa~@
D FAT16 LBA             1068741778 1068965461     223684 [NO NAME]
D FAT12                 1125174205 1125194943      20739 [NO NAME]
D FAT12                 1145408483 1145411362       2880
D Linux                 1249776738 1250274689     497952
```

/dev/crypt was 639 GB, and I put the LVM on top of it, spanning the entire space (eg VolGroup00 = 639 GB). So I'm not really sure what those partitions are; I've never created any of them myself in the past.

/dev/decrypt (as I'll call the luksOpen-ed device) is being scanned right now, though it appears it will take just as long.  I also don't know if Testdisk will find anything: can it find LVM points (Logical Volumes or LOgical Extents)?

---

### Post by touchlikefire on 2009-08-14
Also, prior to your TestDisk suggestion, I did some more research before giving up. Stemming from [this]("http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/") page I issued some commands on **/dev/decrypt** and seemed to make some headway.
```
# pvck -d -v /dev/mapper/crypt1                         
    Scanning /dev/mapper/crypt1                                                 
  Found label on /dev/mapper/crypt1, sector 1, type=LVM2 001                    
  Found text metadata area: offset=4096, size=192512                            
    Found LVM2 metadata record at offset=195584, size=1024, offset2=0 size2=0   
    Found LVM2 metadata record at offset=195072, size=512, offset2=0 size2=0    
    Found LVM2 metadata record at offset=190464, size=4608, offset2=0 size2=0

```

I then opened the block device (/dev/decrypt) with a hex editor, per the article, and copied from the offsets to the end of line marker (0x0A0A) to a text file.  However, when reading the text file, I was not able to reconstruct the information as the author was.

I tried another approach, dd-ing the information from the first sectors of the disk looking for header info.  This was unsuccessful because while I did get information, it was the same information already known to the OS (shown below), so it didn't do me any good:
```
# vgdisplay -v                                          
    Finding all volume groups                                                   
    Finding volume group "VolGroup00"                                           
  --- Volume group ---                                                          
  VG Name               VolGroup00                                              
  System ID                                                                     
  Format                lvm2                                                    
  Metadata Areas        1                                                       
  Metadata Sequence No  1                                                       
  VG Access             read/write                                              
  VG Status             resizable                                               
  MAX LV                0                                                       
  Cur LV                0                                                       
  Open LV               0                                                       
  Max PV                0                                                       
  Cur PV                1                                                       
  Act PV                1                                                       
  VG Size               595.94 GB                                               
  PE Size               4.00 MB                                                 
  Total PE              152560                                                  
  Alloc PE / Size       0 / 0                                                   
  Free  PE / Size       152560 / 595.94 GB                                      
  VG UUID               pLaVMR-myW6-mqLD-mP96-UUzd-xvYw-UMPtbd                  
                                                                                
  --- Physical volumes ---                                                      
  PV Name               /dev/mapper/crypt1                                      
  PV UUID               zxNnox-m2f1-Oijy-93DZ-FE5k-CQAy-i2wFE5                  
  PV Status             allocatable                                             
  Total PE / Free PE    152560 / 152560 
```

I feel like now that I know the offsets of the metadata for the LVs, there must be someway I can manually reconstruct them?

The following commands are available, but I don't have any idea how to use them:
```
he following commands implement the core LVM functionality.

pvchange        - Change attributes of a physical volume.
pvck            - Check physical volume metadata.
pvcreate        - Initialize a disk or partition for use by LVM.
pvdisplay       - Display attributes of a physical volume.
pvmove          - Move physical extents.
pvremove        - Remove a physical volume.
pvresize        - Resize a disk or partition in use by LVM2.
pvs             - Report information about physical volumes.
pvscan          - Scan all disks for physical volumes.
vgcfgbackup     - Backup volume group descriptor area.
vgcfgrestore    - Restore volume group descriptor area.
vgchange        - Change attributes of a volume group.
vgck            - Check volume group metadata.
vgconvert       - Convert volume group metadata format.
vgcreate        - Create a volume group.
vgdisplay       - Display attributes of volume groups.
vgexport        - Make volume groups unknown to the system.
vgextend        - Add physical volumes to a volume group.
vgimport        - Make exported volume groups known to the system.
vgmerge         - Merge two volume groups.
vgmknodes       - Recreate volume group directory and logical volume special files
vgreduce        - Reduce a volume group by removing one or more physical volumes.
vgremove        - Remove a volume group.
vgrename        - Rename a volume group.
vgs             - Report information about volume groups.
vgscan          - Scan all disks for volume groups and rebuild caches.
vgsplit         - Split a volume group into two, moving any logical volumes from one volume group to another by moving entire physical volumes.
lvchange        - Change attributes of a logical volume.
lvconvert       - Convert a logical volume from linear to mirror or snapshot.
lvcreate        - Create a logical volume in an existing volume group.
lvdisplay       - Display attributes of a logical volume.
lvextend        - Extend the size of a logical volume.
lvmchange       - Change attributes of the logical volume manager.
lvmdiskscan     - Scan for all devices visible to LVM2.
lvmdump         - Create lvm2 information dumps for diagnostic purposes.
lvreduce        - Reduce the size of a logical volume.
lvremove        - Remove a logical volume.
lvrename        - Rename a logical volume.
lvresize        - Resize a logical volume.
lvs             - Report information about logical volumes.
lvscan          - Scan (all disks) for logical volumes 
```

---

### Post by chmac on 2009-08-26
I'm in the same boat. I was running 8.10 with an encrypted LVM setup. I tried to install 9.04 64-bit so I couldn't use the dist-upgrade. I went through the installer, got to the partition section, selected the correct partition and said "use as encrypted container", then went to "configure encrypted volumes", it asked me for a passphrase, I entered it. Then it asked me to confirm, I entered again, suspicious. Then I rebooted, encrypted disk is hosed. Appears empty.

pvck -d -v /dev/mapper/sda5_crypt says it can't find an LVM label.

I suspect that the installer overwrote the partition table within the encrypted volume, or maybe screwed the luks configuration somehow.

Personally, I have most of my data backed up, all the critical stuff, so I'm thinking clean install will be the fastest route to a working machine. I'm curious to know if it's possible to recover from this situation though. If I don't find a solution int he next hour or two I'll most likely give up though. :-)

---

### Post by chmac on 2009-08-26
touchlikefire, did you enter a password and then confirm it during the installation process, when you chose "Configure encrypted containers"?

I just did a quick test. I went through the installer to the same point again, this time using a new password ("pass"), now I can luksOpen sda5 with the new password. So it seems like the encryption has been recreated by the installer.

I'm wondering if having the password is enough to recover data. Are there also unique keys which have been overwritten? In which case, recovery is probably not an option at all.

I'm disappointed in the installer. It is not clear that entering a passphrase will commit changes to the disk. Hopefully this is something that can be improved in future versions.

---

### Post by unutbu on 2009-08-26
According to the [LUKS On-Disk Format Specification]("http://www.google.com/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Fcryptsetup.googlecode.com%2Fsvn-history%2Fr42%2Fwiki%2FLUKS-standard%2Fon-disk-format.pdf&ei=lIyVStrqEYbVlAfAotmvDQ&usg=AFQjCNHeE2-0zO_R4Srd43PptaRtdX78yQ&sig2=5kZgeP_KiyMn3YUBsYRdKg") a randomly chosen salt is stored for each key slot. I believe the random salt is added to your passphrase and the two together is then used to decrypt the data block. If either the passphrase or the salt is wrong, then the data is not decrypted intelligibly. 

When the alternate installer re-created the LUKS, it seems likely to me it installed a new random salt to go along with your passphrase. So even if you enter the same passphrase, the act of overwriting the original salt with a new random salt might have nuked your data.

---

### Post by chmac on 2009-08-26
Thanks unutbu, I think you're most likely correct.

Thankfully my backup routine is pretty good, I have verified my data is safe (thanks rsync.net!) and I'm proceeding with the re-install. I'll post a bug somewhere about making the text in the installer clearer. It really wasn't explicit that I was wiping an existing partition by entering a passphrase. :-(

I'm taking the positive, glad to test my restore procedures... :-)

---

### Post by cyberdune on 2009-10-23
i am in the same boat.

How can I manually restore my logical volume groups??

nobody knows? lame... :confused:

using testdisk I definetely find my data. It even sees my lvg's, but lvm2 is not recognizing them anymore. This is for a production machine inacceptable.

now tell me: should I let sleuthkit or testdisk recover 400GB of small data files??? This needs DAYS!!!

I only want lvm2 to recognize my groups. really dissapointed.

regards

---

### Post by chmac on 2009-10-23
cyberdune, you're in the same boat as whom? Are you using LUKS encryption? If you've hosed your encryption, you most likely won't see anything in testdisk.

I think restoring LVM partitions is tough. I'd say your fastest route might be to use testdisk. I'm no expert though, there might be other information on this forum.

If you post your specific circumstances (in a new thread if it's not relevant here) then you might get some more information.

---

### Post by cyberdune on 2009-10-24
> **chmac said:**
> 
I suspect that the installer overwrote the partition table within the encrypted volume, or maybe screwed the luks configuration somehow.


ja, this, didnt think further. certainly nothing to do anymore from this point here... despite digging in certainly (murphy ;-) ) too old backups :(

:popcorn:

---

