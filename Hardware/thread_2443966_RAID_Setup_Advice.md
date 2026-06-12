---
title: "RAID Setup Advice"
date: 2020-05-22
forum: Hardware
---

### Post by invex092 on 2020-05-22
Looking for general advice on setting up Ubuntu Desktop with a RAID. I'm getting confused with the different options I'm seeing after researching: MDADM, ZFS, Hardware and I don't totally understand the difference between them. 

My setup is 5 hard disks: 4 x 250GB Samsung SSDs and 1 x 1TB HDD

When I set out to start, I wanted to run a hardware RAID: 4 SSD drives as a RAID 1+0 and install/run Ubuntu off that drive and use the regular HD for media storage. I have a Gigabyte GA-P55A-UD3 motherboard with Intel RST so originally I setup the RAID through Intel RST but the Ubuntu installer complained at the end about not being able to setup MBR so that didn't work. Would it be possible to just install the MBR on the regular SATA non-raid drive and have that Intel RST RAID 1+0 setup for the OS partition? 

When I ran into that issue and started Googling I started exploring software RAIDs (ZFS and MDADM). In general, for performance, would it be recommended to use ZFS over using Intel RST? I use ZFS for a FreeNAS server and like it a lot, but thought a hardware RAID would be better for this setup. Any advice as to which setup would be recommended would be appreciated, thanks!

---

### Post by TheFu on 2020-05-23
You can do reading about the differences in RAID options.

HW-RAID should be avoided for most home users.  When using it, a quality RAID card is required to make it worthwhile. One with on-board batteries to ensure any power failure doesn't prevent those last few seconds of writes actually get written.  You'll need 2 of those cards, from the exact same manufacturing lot to ensure the chips aren't different.  Vendors change the chips, which changes the read-write of data on the disks, so a spare RAID controller from a different lot may not be able to read the existing data when the HBA fails.  HW-RAID means your data is tied to that, exact, specific, card. That's a bad thing.

Fake-RAID is what cheap RAID cards and motherboards provide.  These have all the liabilities of a HW-RAID card, but none of the added safety and the performance usually sucks.

SW-RAID is very fast these days, since all our CPUs are crazy fast now.  SW-RAID can be moved between systems and isn't tied to the disk controller or chips or really the version of Linux used.  I've moved SW-RAID arrays between 3 physically different systems and changed Linux OSes.  What's important is that mdadm is used.  Well, that WAS important in the passed.

ZFS is the new-kid from a Linux perspective, though it has been available for Linux perhaps 10 yrs.  It is a different way of thinking.  Ars has had 2 articles about ZFS recently written by a guy who works/worked for the company behind FreeNAS.  
[https://arstechnica.com/information-technology/2020/05/zfs-101-understanding-zfs-storage-and-performance/](https://arstechnica.com/information-technology/2020/05/zfs-101-understanding-zfs-storage-and-performance/)
[https://arstechnica.com/gadgets/2020/05/zfs-versus-raid-eight-ironwolf-disks-two-filesystems-one-winner/](https://arstechnica.com/gadgets/2020/05/zfs-versus-raid-eight-ironwolf-disks-two-filesystems-one-winner/)
[https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/](https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/)
I've met Jim and spoke with him at SouthEast LinuxFest.  Pretty sharp guy.

ZFS RAID and mdadm RAID are not compatible.  You'd never use both on the same system.  The view you've seen of ZFS through FreeNAS is probably just through the web-GUI.  That really isn't the way you'd use it on Ubuntu.

You didn't mention it, but LVM supports certain RAID levels too. Might be something you'd like to spend 15 minutes researching. [https://serverfault.com/questions/435839/create-raid10-with-lvm](https://serverfault.com/questions/435839/create-raid10-with-lvm) RAID10 through LVM.

BTRFS also supports RAID, I think.  I'd never use it, but perhaps you or some lurker in 12 months would?  Spend 15 minutes doing some research about it as well.  Just know that redhat has deprecated btrfs for a number of reasons.

I have no idea was Intel RST is and didn't look it up.

If I were just starting out, I'd probably use ZFS for the data and LVM for the OS.  Really, the number and types of disks you have seems odd.  I would have expected 1 SSD and 4 HDDs, then it would be very clear where the OS should go (SSD) and the ZFS would be on the HDDs.

Whenever using any storage, always, always, always setup a GPT partition table and at least 1 partition. Don't write the RAID directly on the whole disk.  Problems can arise where NOT having a partition table just makes things more complex.  Also, when sizing the partition, choose a size that is exactly what you want. Think about the future when 1 of the RAID members fails and needs to be replaced.  You probably won't buy exactly the same model storage, so you'll need to know the exact size for the partition to make it match what is existing.  Storage size math is a little fuzzy based on the vendor. 250G isn't always 250G with every vendor.  Make certain you can always put a partition sized exactly on the new storage.

As for file system layouts.  Please don't use over 30G for /.  There's no need and it makes backups, system upgrade and a few other things more difficult. I have entire desktop systems that have been moved forward since 10.04 with 17G of storage.

As to how you'll get the OS to install onto a RAID10 setup, I haven't any clue.  Ubuntu's weak in the storage management during installation.  I don't think it will boot from RAID storage, so the /boot/ and /boot/EFI areas cannot be anything except simple partitions.  

20.04 has experimental support for ZFS as the OS storage.  I installed using that inside a VM.  Don't recall any options being available, except "use ZFS (Experimental)".  I haven't used ZFS on Linux and my Solaris use was 12+ yrs ago.  Don't know how easy it is to change ZFS modes after the initial choices are made.  Most people use ZFS for RAIDz2. Don't know how often other modes are used.

---

