---
title: "large hhd sizes vs. formatting in linux"
date: 2013-01-12
forum: Hardware
---

### Post by thane1 on 2013-01-12
Recently had occasion to format a 3TB drive using my Gparted Live disc.  The system it was going into required the gpt option be used to allow the system to recognize a ntfs drive larger than 2TB.  I'm thinking of adding another internal sata drive to my box and this got me thinking.  What is the largest size hdd ubuntu will recognize these days and what special formatting procedures might be needed to do this?  Actually I'm on 64 bit linux mint 14.1 based on the newest ubuntu release.  Don't seem to be able to find any info anywhere (including the gparted site) to shed light on this.  Many thanks.

---

### Post by TheFu on 2013-01-12
> **thane1 said:**
> Recently had occasion to format a 3TB drive using my Gparted Live disc.  The system it was going into required the gpt option be used to allow the system to recognize a ntfs drive larger than 2TB.  I'm thinking of adding another internal sata drive to my box and this got me thinking.  What is the largest size hdd ubuntu will recognize these days and what special formatting procedures might be needed to do this?  Actually I'm on 64 bit linux mint 14.1 based on the newest ubuntu release.  Don't seem to be able to find any info anywhere (including the gparted site) to shed light on this.  Many thanks.

Gparted and parted support all the newest GPT format capabilities from what I've read.  GPT is required for HDDs larger than 2TB in size. This replaces the aging MS-DOS format (or MBR) header.  I think Windows7 is the version from Microsoft to support this, though it might be possible to load a WinXP OS into a "primary" partition within the first 2TB. 

As to what is the largest size HDD that Ubuntu will recognize, I don't know, but you are safe with 4TB.  However, as disks get larger your risk of failure increases.  There is a reason that most enterprise HDDs are less than 750GB in size - reliability.  Plus most of the larger HDDs do not include SATA instructions that were commonly provided in all HDDs just a few years ago which are highly, highly, highly recommended for RAID use.

You are asking about hard disk size, but not about **partition sizes.**  Normally, file systems go onto a partition, which every HDD will have.  There is ZFS - **z**etabyte **f**ile **s**ystem which you may run on Linux. That should give you an idea of how large the file systems supported are. 

I'd also bet that if you googled for** file systems limits**, a maximum size would be listed for the top 20 of them. [https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)  It appears if we are running modern file systems, that the size of either an individual file or all the files are not a concern.  I know of enterprises where having a 20TB file system (using RAID10 striped disks) is fairly common.

Now I'm curious about your specific HDD size limit question.  I do not think there is any build-in limitation beyond what 64-bits can address - a huge, huge, huge number.

I think the GPT limits would matter most. Wikipedia [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table) says, > GPT allocates 64 bits for logical block addresses and therefore allows a maximum disk and partition size of 264&#8722;1 sectors. For disks with 512-byte sectors, that would be 9.4 [ZB]("https://en.wikipedia.org/wiki/Zettabyte") (9.4 × 1021 bytes)[[1]]("https://en.wikipedia.org/wiki/GUID_Partition_Table#cite_note-UEFIDrivePartitionFAQ-1")[[2]]("https://en.wikipedia.org/wiki/GUID_Partition_Table#cite_note-Redmondmag64bitQuestion-2") or 8 [ZiB]("https://en.wikipedia.org/wiki/ZiB")&#8722;512 bytes (9,444,732,965,739,290,426,880 bytes or 18,446,744,073,709,551,615 (264&#8722;1) sectors × 512 (29) bytes per sector).

Whether the hardware is recognized is a different question, all together.
"Whether the hardware is recognized is a different question." ;)

Interesting question.

---

### Post by thane1 on 2013-01-13
Thanks TheFu for the reply.  A lot of info there.  My present box has a 1TB drive in it, multi-partitioned and included a good sized /home and slightly larger /backup partitions.  With Vbox .vdi files and my regular useage I've just had to delete my /backup partition to extend the /home partition.  So I'm now in need of another /backup at least as large as my new /home and hence the need for another hdd.  Probably a good thing, since I don't usually like to have my /home and /backup partitions on the same hdd in case it gets toasted.

Haven't used raid for a few years.  Just prefer to do backups manually now.  However to the original post I was toying with the idea of maybe springing for a drive of one or two TB in size and that got me to wondering what linux was actually capable of handling.  Your point of size vs. reliability seems wise.  Think I'll probably limit myself to another 1TB drive (possibly an external).  cheers

---

### Post by TheFu on 2013-01-14
> **thane1 said:**
> Haven't used raid for a few years.  Just prefer to do backups manually now.  However to the original post I was toying with the idea of maybe springing for a drive of one or two TB in size and that got me to wondering what linux was actually capable of handling.  Your point of size vs. reliability seems wise.  Think I'll probably limit myself to another 1TB drive (possibly an external).  cheers

**RAID has nothing to do with backups. **RAID is for high-availability, backups to other media are still required!!!

I'd also point out that many people run 2TB and larger drives with Linux and have not seen any issues different than the smaller 500G drives.  Heck, I have 2x2TB HDDs in a RAID1 setup right now with a 3rd HDD for automatic, nightly, backups using rdiff-backup.  RAID does not protect against viruses, file corruption, or human stupidity. That last one happens the most around my house. ;) Having great backups have saved my systems at least once a year the last 5+ yrs.

I also have a bunch of 1TB drives.  I only use "green" HDDs for backup media or for large data files that I do not care about (TV recordings), but lots of folks use the cheap, large HDDs for lots of important data too. YMMV.

---

