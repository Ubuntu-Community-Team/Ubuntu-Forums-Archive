---
title: "HOWTO make Mdadm work with GPT Partitioned 3 TB Drives"
date: 2014-03-06
forum: Hardware
---

### Post by mcapaldo on 2014-03-06
I am no stranger to mdadm or TB Drives, I have 6 x 2TB Drives in Raid 5.  But running out of space so I need to upgrade drives.  

Now I jut got a deal on 3 x WD 3 TB Drives.  Gonna setup another pc with Ubuntu LTS 12.04 As with machine above.  My questions are:

1. Will I need a pc that has UEFI bios just to recognize the drives?  I can I use a 1-2 yr old MB that recognizes the 3TB Drives.  Not looking to boot off those drives.

2. Will I have to use GPT partitioning on each 3 TB Drive, then setup the mdadm raid5 array?

3. Does mdadm in 12.04 LTS Server support 3TB Drives and GPT partitions using raid 5?

4. Could I get away with an older MB but using a PCI E Raid Card? with say 8 ports.  If so what are my options (for pass thru so mdadm will see and use the drives)?  I am trying to be on a budget.  I realize that on an older MB SATA 6Gbps will only get about 5Gbps as it will saturate.  

5. I can then install smartmon and ssmtp to notify me of any problems.  Done that before.

---

### Post by TheFu on 2014-03-07
mdadm doesn't care about GPT at all. A partition is a partition.

If you want to boot off a GPT drive, then things become more complex.  I'm booting a 4TB HDD wiht GPT using BIOS. Some BIOS do not work with GPT - it is generally accepted that those BIOSes are checking for things they shouldn't be checking.  So ... the boot question you have answer is "it depends."

Oh - and I only run 12.04 and stopped using RAID5 - there is a danger called the "write hole" with it.

As to whether you need GPT partitioning to use RAID - that is up to you. It is possible to not have any partitions at all and use RAID.  I prefer to have the partitions as a reminder that the disks are not empty. If the HDDs are over 2.1G (approximately), then to access more storage, you'll want GPT.

If you want lots of performance from your disks, get a good LSI SAS RAID card. I've seen them for $300-$400.

Spinning HDDs won't come anywhere near the SATA-III 6Gps bandwidth.  Each drive will top out around 100-120MB/s ... so the best performance you can hope for it 300MB/s (you won't see that) ... nothing close to 6Gps.  

There is no way to be assured of alarming for disk subsystems. Sure, mdadm will email an issue about a failed disk - but will you see that email?  

RAID does not replace BACKUPS!!!!   A guy at my LUG just this week was trying to restore a client's failed RAID setup. They didn't do backups and lost everything.  Backups are 1000x more important than RAID.

---

### Post by p2bc on 2014-03-07
I had my own [issue]("http://ubuntuforums.org/showthread.php?t=2209609") with RAIDs lately, as well as [issue 2]("http://ubuntuforums.org/showthread.php?t=1991404"). The second one might be a good read for you.

Either way I think, there is a better way to tackle your issue. Specifically expanding your capacity. I can't take any credit for nothing that follows, and it is what lead to me reworking my setup with my drive configurations, and which touches appon in my first "issue"(see up bove). I had RAID10, RAID5, and RAID6, none of them quite did it for me, for one reason or the other, until I saw this Video that clarified terms that I had seen but could not get my head around.

The video was from Shawn Powers (Linux Journal) from [CBT Nuggets - Ubuntu]("http://www.cbtnuggets.com/it-training-videos/course/ubuntu/10594") series. Where he explains LVMs and RAIDs, the light was turn on so to speak . Why they are good seperately, but even better together.

LVM - Logical Volume Management - Is a group of drives that are treated like one single partition.

So if you have a LVM labeled "system" and system consisted of a 10G, 40G, 80G drives.
system = [10G + 40G + 80G] = 130G

So if some point down the road you need more space you simple add what ever is avaible at the time or cheap, say 1TB.
system = [10G + 40G + 80G + 1T] = 1130G

But what if the 80G of system LVM was not a drive but rather a RAID1(or RAID5, RAID6,...). Nothing, actually to the LVM it would seem no difference. So if they were all RAIDs, same thing, but now you would have parity. If a drive fails your data is not lost. 

Ok, but then why not make a RAID of all the drives. Simple, because it does not give the fexiability of the future availability, In  a RAID all drive partitions must be the same size. So lets say you have 4 2TB drives, because you could get them for $80. So you build a RAID1, or RAID10, or RAID5, or RAID6 whatever tickles your fancy for whatever reason. A year goes by and drive fails so you go to replace it and 3TB are selling $80, and 2TB are actually $120. You buy the 3TB but only end up using 2TB, 1000G not being used which you paid for, simply because your remainding drives that you bought only a year ago are 2T.




So my suggetion, it suck right now, but rebuild your system using LVM, with RAID1 for the section, and this way down the line as capacity grows and gets cheaper you can simply add to it rather that changing it each and every time. Independent of the GPT, UEFI or BIOS.

---

### Post by TheFu on 2014-03-07
@p2bc - some excellent points in there.  I would like to point out that the ONLY TIME I'VE EVER HAD DATA LOSS in my life was when using LVM to span data across 3 drives.  The middle drive failed, I was without backups and lost all the data on all 3 drives, not just the middle one. Tried to recover the data for about 6 months ... it wasn't THAT important.

I'd also point out that I had a RAID1 drive fail here a few weeks ago.  Bought a replacement, different brand, the same day. Removed the failed HDD from the mdadm array, took down the machine, swapped in the new HDD, partitioned it identical to the failed HDD and added it back to the array.

Oh - and I have backup religion these days, so all that data on the RAID was still backed up elsewhere. I sleep really well at night - before I thought I was being smart, but didn't understand the risks I was taking with my data.

---

### Post by p2bc on 2014-03-07
@TheFu -  Yeah, a simple LVM is the same as RAID0, a higher chance of failure with ever drive added, except for the limitation of the partitions being the same size. I use to use LVMs on a RAID partition, which makes little sence, but it seemed to be what all the cool kids where doing. It was after watching the Nugget that I did a facepalm and said, "now that make more sence". A real eye openning experience. Not to mention my head hurt for a while after, I smacked it hard. I guess it is a good thing, means I won't forget it.

---

### Post by TheFu on 2014-03-07
I use LVM all the time these days too. Mainly on VM servers, but also with RAID>1 configs.  Removed all RAID5 here about a year ago, only have RAID1 these days.

For situations with large media collections, there are other options that might make more sense - I've never used them, but they are great at making more of the storage available for actual data, while handling 1 or 2 disk failures. **SnapRAID** is one of those options. I don't understand how it can possibly work ... but reputable people like it.
I don't use RAID for my media collections. Simple mirrors via **rsync** delayed by a few days. Back when I used optical media, parity files were included on those backups - saved a few failures the last 8 yrs. par2 is that tool.

Just sharing options. There are others too.

---

