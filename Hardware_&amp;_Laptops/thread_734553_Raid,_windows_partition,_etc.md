---
title: "Raid, windows partition, etc"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by DrObviousSo on 2008-03-24
This request is not for a quick technical question, so I really appreciate anyone who reads through and can give me some advice.

I had a HD failure today, and I decided to just go ahead and and set up a RAID 1 system.  I currently have a working 120 gig hard drive.  This has a 20 gig windows partition, a 10 gig Ubuntu partition, a 1 gig swap partition, and a NTFS partition that takes up the rest of the space.

I'm going to be getting 2 500 gig HD's.  I would like to:
1)Copy over the partitions from the working HD, preserving or rebuilding the boot structure that's in place
2)Enlarge, if possible, the Ubuntu partition to 20-30 gig
3)Enlarge the NTFS partition to take up the rest of the space, or create another NTFS partition.  If I can manage to salvage some data from my 250 gig HD, that data will go here.  If not.. I'm sure I'll fill it up eventually.

I [have this mobo]("http://www.ecsusa.com/ECSWebSite/Products/ProductsDetail.aspx?detailid=673&DetailName=Specification&MenuID=44&LanID=9"), which claims it supports RAID 1, but I've read some stuff online that says if there are windows drivers for a raid system, it won't work with ubuntu.

Can anyone tell me the tools I'll need to accomplish steps 1-3?  I think I have a clue about some of it, but I've run into some conflicting info, so a fresh, human voice would be much appreciated.

---

### Post by Vermind on 2008-03-25
Hi,
I am running Ubuntu Feisty using software RAID (dmraid).
I have 2 160 GB disks that used to be part striped, part mirrored. Nowadays both my boot and root are mirrored. To change to striped, change the raid level to 0 on the desired partition group in  /etc/raidtab.

My disks look like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  fd  Linux RAID autodetect
/dev/sda2              13       19457   156191962+   5  Extended
/dev/sda5              13         136      995998+  82  Linux swap / Solaris
/dev/sda6             137       19457   155195901   fd  Linux RAID autodetect

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96358+  fd  Linux RAID autodetect
/dev/sdb2              13       19457   156191962+   5  Extended
/dev/sdb5              13         136      995998+  82  Linux swap / Solaris
/dev/sdb6             137       19457   155195901   fd  Linux RAID autodetect
```

And they are set up in /etc/raidtab like this:


```
# / (reiserfs)
raiddev                 /dev/md1
raid-level              1
nr-raid-disks           2
nr-spare-disks          0
chunk-size              32
persistent-superblock   1
device                  /dev/sda6
raid-disk             0
device                  /dev/sdb6
raid-disk               1

# /boot
raiddev                 /dev/md0
raid-level              1
nr-raid-disks           2
nr-spare-disks          0
chunk-size              32
persistent-superblock   1
device                  /dev/sda1
raid-disk             0
device                  /dev/sdb1
raid-disk               1

```

Now, there are lots of howtos for setting up software RAID in Linux, if You google software raid , dmraid or raidtab. The good thing about software RAID is that it doesn't really matter which motherboard You have, and drivers for RAID are not an issue.
The approach using the windows drivers is different: I never tried it. I have been told that it depends on Your RAID controller and whether it has drivers for Linux or not. If not, Your Linux will not recognize Your RAID disk group at all, if You set it up with the BIOS RAID utility. 
On the other hand, using software RAID Your windows will not be able to use RAID for its partitions, since it will just see the partitions as separate. Also accessing a striped Linux partition from windows in non-raid mode is not recommended. 

Now, should You choose software RAID, the procedure for Your step 1 is as follows:
1. google how to set up Your RAID partitions with dmraid
2. mount a raid partition to say /media/raid-root
3. ```
cp -rxp / /media/raid-root
```
4. if You have a boot partition, copy it over to its new destination partition
5. edit /media/raid-root/fstab to change the root and boot and others
6. edit raidtab and fstab some more if You intend to remove Your old hd
7. create partitions for the windows file systems and copy them over the same way, or you might copy them as disk images after creating the partitions, like so:
  cat /dev/windows-partition > /dev/new-windows-partition
Make sure they work by mounting them before removing anything.
8. Remember to set bootable flags and prepare to fix some boot problems with windows.
9. Remember to install grub on the new hard drives. If Your boot is mirrored like mine, You can install grub on both hard disks, telling both grubs that they are on hd0. this way if one boot partition ever fails, the second one will take over. this can be done with the grub interpreter. You can google up how to setup grub with RAID and mirrored boot to find some solutions.

Steps 2 and 3 are not really very necessary, if You create big partitions to start with on the new HDs and copy over the files. If You copy the windows partitions as disk images, and want to do the resizing of partitions, I suggest using gparted and if that is not working, to read up on ntfsresize. The basic procedure is to use fdisk to _remove_ a partition (but not any of the data and not pressing write yet), then creating the partition again, in the same position with the same type, but as large as You want to make it. Then write changes, and use ntfsresize to expand the ntfs file system to use the new space that the larger partition now allows. The reverse order applies for shrinking a partition: First ntfsresize the file system to a smaller size, then re-create the partition using fdisk with a smaller size. Never create a partition smaller than the filesystem. it may cause data loss or loss of the whole partition. If You mess up badly, use the testdisk utility on a livecd to recover the partition table.

I hope this helps.

---

### Post by DrObviousSo on 2008-03-25
Thanks for the reply.  I'm still considering my options, but that looks like it'll give me everything I need to know.

---

