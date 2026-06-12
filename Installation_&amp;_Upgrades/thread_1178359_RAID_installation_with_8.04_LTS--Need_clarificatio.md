---
title: "RAID installation with 8.04 LTS--Need clarifications on process"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by questant on 2009-06-04
I am setting up a system to work as a file server on a low volume access network.  The system has the following specs:
Motherboard:  Abit VP6
BIOS:  Award Modular v.6.00PG
Built-in RAID controller:  HPT370
Memory:  1GB
IDE connected drives on Primary IDE1:  2 CD drives:  Lite-On LTR1210B CD Burner (Master); IDE/ATAPI CD-ROM reader (Slave)
Nothing connected on Secondary IDE
RAID Primary:  2 matching Western Digital WD5000JBRTL 500GB drives

Began the installations with 9.04.
Desktop, Alternate and Server CDs all failed for one reason or another (including inability to refind the very CD drive from which the installation was being run during the hardware search, aborting installation to a "Busy Box").
Read 9.04 postings and decided to go back to 8.04 LTS for the install using the Alternate CD (there are two other 8.04 LTS systems acting as servers in the network).

Installation proceeds nicely through the partition sequence.
Made choice to Partition Disks, beginning with the first disk (the second to this point has remained untouched), setting 'use as' to "physical volume for RAID".

It yielded the following screen:
--------------------------------------------
                    Partition Disks

This is an overview of your currently configured partitions and mount points.  Select a partition to modify its settings (file system, mount point, etc.), a free space to create partitions, or a device to initialise its partition table.

        Configure software RAID
        Guided partitioning
        Help on partitioning

        IDE3 Master (hde) - 500.1 GB WDC WD5000AAKB-00H8A0
              #1 Primary 497.0 GB B K raid
              #5 logical    3.1 GB   f swap   swap
        IDE3 slave (hdf)  - 500.1 GB WDC WD5000AAKB-00H8A0

Undo changes to partitions
Finish partitioning and write changes to disk
---------------------------------

(I did not configure the second (slave) disk and from reading documents below, I am under the impression I must also configure the second (slave) drive to match the first BEFORE committing to the Finish ... link.  I have since returned to the above screen and am preparing to configure the slave drive as well, pending response from this post)

 -- However, with the configuration as above (slave unconfigured) I selected Finish ... and received the following screen
----------------------
                           Partition Disks

Before RAID can be configured, the changes have to be written to the storage devices.  These changes cannot be undone.
When RAID is configured, no additional changes to the partitions in the disks containing physical volumes are allowed.  Please convince yourself that you are satisfied with the current partitioning scheme in these disks.

The partition tables of the folloing devices are changed:
     IDE3 Master (hde)

     The following partitions are going to be formatted:
            partition #5 of IDE3 master (hde) as swap

     Write the changes to the storage devices and configure RAID?

-----------------------------

Frankly, the statement "these changes cannot be undone" is both disturbing and unclear.  I can understand that committing to a RAID configuration locks the disks in and they could not later be modified.  That is somewhat different than saying something cannot be undone.  Grinding a rock to powder is permanent.  The rock will not be reconstituted.  It cannot be undone.  Is that also true for these drives?  Is there some low-level format routine being done to the drive that irretrievably destroys the manufacturer's low-level format as delivered?  Once committed to this RAID configuration are these drives irretrievable for any other purpose later, such as moving them to a standard IDE controller in a different machine, repartitioning and reformatting them according to different purposes?  Does it mean one could not clean them off and create a new RAID system on them from scratch?  "Cannot be undone" implies they cannot be reconstituted into any other configuration, period.  I would expect something like "Once these changes are committed to the drives, no further modifications are possible unless one removes the existing partitions and starts over."

Please forgive my paranoia.  Over the years I've rationalized irreversabilities into something less than they were a few times and paid the price accordingly.  An ounce of prevention ...

Clarification on this issue would be greatly appreciated.  I've never set one of these systems up before and would rather do it right the first time.

In addition, I'm not sure from my research if the HPT360 is indeed a FakeRAID or a true hardware RAID.  I've had implications of both in different articles.

Thanks in advance for any clarifications to the above questions and confusions.

Reading list so far:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[http://www.dalouche.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/](http://www.dalouche.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/)
[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)
[http://www.murty.net/ataraid/](http://www.murty.net/ataraid/) (oriented to RH)
[http://www.murty.net/ataraid/nativeraid.html](http://www.murty.net/ataraid/nativeraid.html)  (oriented to RH)
[https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID) (U-7.04)

None of these discussions quite matches the installation sequence I see on screen with the 8.04 Alternative CD and none reference the above warning statement and/or describes its meaning.

---

### Post by cariboo on 2009-06-04
Anything that can be done as far as partitioning goes, can be undone. I've used the FakeRaidHowto several times and never had a problem. 

I set up the distribution on an ide drive and used fake raid for storage. Remember raid is not a substitute for a good backup plan. Raid only protects you from a failed hard drive. It can not protect you from corrupted data.

---

### Post by questant on 2009-06-05
Thank you Cariboo (Williams Lake -- Canada? Washington? Ohio?  Not Ohio).  Your remark following the "anything can be undone" statement represents exactly what I want to do.  The machine in question was set up over a year ago with 8.04LTS as a Shop Desk internet access point for research on computer configurational and repair issues.  I would like to keep the installation on the IDE drive (which functions admirably).  I would like to use the RAID (obviously fakeRAID -- I've clarified that issue) connectors for two mirrored data-storage-only drives.  I don't want to install to them or run Ubuntu Linux from them (I wouldn't mind adding some additional swap space to them but am not inclined to do so at the moment).

Virtually all the info I find gives instructions for installing to the RAID drives and NOT how to partition and activate them as mirrored storage units.    Your boot-to-IDE-use-RAID-as-storage configuration is EXACTLY what I'm after.  Can you direct me to an appropriate discussion of that approach.  It would be deeply appreciated.

I totally agree about RAID, mirroring and data protection.  I write a computer column for a local paper and hammer backup over and over.  The key is redundancy.  The mirror provides active redundancy to the file server but is not a substitute for backup.  I would also note, failure to properly write data is not just a problem for RAID.  It is ubiquitous.  Any system and any fs can blow it writing data any time.  A mirror of corruption is the wrong kind of redundancy.  The point of the RAID in my situation is on-the-fly-failsafe for drive failure.  It must be  must be addressed immediately.

With the 8.04 Alternate CD I was at the partitioning screen with the IDE drive with U on it was disconnected.  Is there any reason why I could not disconnect the IDE again, run the installation CD, do the partitions on the matching drives and then abort the installation, replug in the IDE and then continue to identify and mount the already partitioned drives?  Is that "going around Robin Hood's barn" to get at something much easier to perform.

Sorry to bother you all again with this but I'm in learning mode here.
Thanks in advance for any response.  I know I can figure this out "stick-shift" but, unfortunately, at the moment time of of the essence.  The hurrier I go the behinder I get.
Thanks again.

---

### Post by questant on 2010-08-26
Solved this issue by installing Debian instead.

---

