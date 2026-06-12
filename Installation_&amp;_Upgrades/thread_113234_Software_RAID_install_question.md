---
title: "Software RAID install question"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by rick333 on 2006-01-06
I have an AMD64 dual-core machine with 3 SATA disks: 1 x 80GB, 2 x 160GB, and I want to implement RAID-1 to mirror the 160s. Plan to install Ubuntu and WinXP on the 80GB drive and use a mirrored /home and maybe a shared (between WinXP and Ubuntu) mirrored fat32 partition on the 160GB drives. I have also posted a related question here: [http://www.ubuntuforums.org/showthread.php?t=113229]("http://www.ubuntuforums.org/showthread.php?t=113229")

I've done a bunch of reading about LVM, EVMS, and md, and I'm trying to figure out which to use and in what combination. Some questions:

1.  Is it possible to install Ubuntu and use EVMS alone to create RAID-1 partitions, or must I use md to create the RAID partitions during the install process? 

2. Should I use EVMS or LVM to manage the volume sizes?

3. Does the Ubuntu install process use EVMS or only LVM?  If I use EVMS instead of LVM, when do I create EVMS objects? If they must be created after Ubuntu installation, I assume that means that I would have to use md to setup the RAID partitions during installation. Is this correct?

4. It seems that it would be just unnecessary complication to use LVM and EVMS, and that one would only use both if migrating from LVM to EVMS in an existing installation. Is this correct?

I'm a bit confused and would greatly appreciate some help.

---

### Post by Zafrusteria on 2007-10-19
You can use Software RAID without EVMS. This will work for Ubuntu by just using mdadm. AFAIK M$ windows cannot access Linux software RAID or EVMs or LVM volumes. The RAID from the motherboard will also not be able to access the Linux Software RAID. I'll be really glad to be wrong here as I want to do something similar.  Windows is the problem.:( 

You have some options.

Make sure you have everything backed up !!

Just use software RAID, that is no EVMS or LVM and mirror the whole disk. You can do this when installing Ubuntu use the alternate disk. You can use the partitioner to partition the hard disks and mark the partitions on the 160G drives for use with RAID. 
You then get an extra option when you return to the partitioning screen. The option to "Configure RAID". Just follow the prompts and set up the RAID1 device to be the two 160gs and then when you return again to the main partition screen you will see a new RAID1 partition that you can setup with the ext3 or reiserfs etc and its mount point just like you can for a regular partition.
(I really must write a long descrition HOWTO for this) 

I've never got on with EVMS sorry. To manage the volume sizes you can use LVM. create a physical volume on the complete 160 disk by creating a partiton the  size of the drive. add both to a volume group and then create a mirrored logical volume. Using LVM you can add more than one logical volume also you can  resize as necessary. I use reisersfs as you can expandthe partition with the partition mounted. :-) Its only takes a few seconds to add another 50G.

Hope that helps, but these links will help you more.

This is a great HOW once you have an understanding of LVM :-) [http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

This is a great HOWTO to read with the one above [http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Cluster_Logical_Volume_Manager/index.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Cluster_Logical_Volume_Manager/index.html)

---

### Post by njparton on 2007-10-19
You'll have to get your software raid card installed first which may or may not require compiling drivers etc.

I have a Highpoint Rocket RAID 2210 card and it's not recognised by default even though drivers have been available for the linux kernel 2.4.x and later.

I'm therefore going to upgrade to a 3ware 9650SE (hardware raid) card when I build my home NAS device around ubuntu. 

Software raid will be heavily cpu dependant and I'm only planning on using a low end AM2 sempron. 

You may also find it easier in the long term if you switch to hardware raid. Price is a big issue though...

---

