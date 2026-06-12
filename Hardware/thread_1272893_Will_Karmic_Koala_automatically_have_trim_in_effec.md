---
title: "Will Karmic Koala automatically have trim in effect ..."
date: 2009-09-22
forum: Hardware
---

### Post by josephellengar on 2009-09-22
on computers with a SSD?  Just curious.

---

### Post by josephellengar on 2009-09-27
Bump.  C'mon, anybody?

---

### Post by hanzomon4 on 2009-09-27
What is trim?

---

### Post by MellonCollie on 2009-09-27
> **hanzomon4 said:**
> What is trim?

[http://en.wikipedia.org/wiki/TRIM_(SSD_command)](http://en.wikipedia.org/wiki/TRIM_(SSD_command))

---

### Post by MellonCollie on 2009-09-27
> **idigchess said:**
> on computers with a SSD?  Just curious.

From the above link...

> TRIM has been implemented in Linux 2.6.28

---

### Post by NormanFLinux on 2009-09-27
The Ubuntu and Kubuntu Netbook editions will be compatible with netbooks.

---

### Post by jpeddicord on 2009-09-27
> **NormanFLinux said:**
> The Ubuntu and Kubuntu Netbook editions will be compatible with netbooks.

Think you might be in the wrong thread. :)

---

### Post by NormanFLinux on 2009-09-27
Really? I was under the impression Karmic is going to offer trim for small form factor devices and those are one of the ways its being developed.

---

### Post by andrewabc on 2009-09-27
> **MellonCollie said:**
> From the above link...

Yes it is implemented in Kernel, but will it work with default install or do SSD users have to hack a bunch of stuff to get it to work?

---

### Post by josephellengar on 2009-09-27
> **MellonCollie said:**
> From the above link...

Trim needs to be implemented at the OS level, not just at the kernel level.

---

### Post by nhasian on 2009-09-27
one of the reasons for me waiting to get an SSD drive (besides the price drop this Q4) is for ATA-TRIM to be ready out of the box.  Hoping to see that by the time Karmic is launched.  I know its in the kernel but wether or not its enabled by default is a different story.  How can someone with an SSD drive check to see if ata-trim is enabled?

---

### Post by josephellengar on 2009-09-27
> **nhasian said:**
> one of the reasons for me waiting to get an SSD drive (besides the price drop this Q4) is for ATA-TRIM to be ready out of the box.  Hoping to see that by the time Karmic is launched.  I know its in the kernel but wether or not its enabled by default is a different story.  How can someone with an SSD drive check to see if ata-trim is enabled?

Yeah, that's exactly what I want to know.  That's why I started this thread.

---

### Post by hugmenot on 2009-09-27
I have a Samsung OEM SSD in my X301 Thinkpad. Now, after reading [this section]("http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=19") of the later Anandtech article I got fairly upset.
No TRIM for me in any case I guess ...

But then I found the brutish, terrifying method. And I think I&#8217;m gonna try it tomorrow:

[http://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](http://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by Paqman on 2009-09-27
According to Theodore Tso, the guy behind ext4:
> 
**Ext4 has support for the ATA TRIM command**, which allows filesystems to inform SSD’s that blocks have been deleted and do not need to be taken into account by the SSD’s garbage collection and wear-leveling algorithms. Unfortunately the ATA TRIM command hasn’t been finalized yet, and so **(as of today) there are no drives, including Intel’s SSD’s that actually support the ATA TRIM command; and for this reason Linux’s block device layer does not currently issue the ATA TRIM command**, since there haven’t been any devices to test the command. So at the moment, ext4 informs the block layer that blocks that belong to deleted files can be discard, so **once TRIM-capable SSD’s become available, and the Linux block layer actually sends the TRIM command to the hard drives, everything will be all set to go.**


[Source]("http://www.linux-mag.com/id/7272")

---

### Post by josephellengar on 2009-09-27
> **Paqman said:**
> According to Theodore Tso, the guy behind ext4:


[Source]("http://www.linux-mag.com/id/7272")

The gen 1 drives did not have support, but the gen 2 drives do.

---

### Post by Paqman on 2009-09-27
> **idigchess said:**
> The gen 1 drives did not have support, but the gen 2 drives do.

Fair enough. That article is 6 months old, which in SSD years is a looong time.

(SSD-years being a bit like dog years, see.)

---

### Post by hugmenot on 2009-09-27
> **Paqman said:**
> Fair enough. That article is 6 months old, which in SSD years is a looong time.

(SSD-years being a bit like dog years, see.)

In the month-old Anandtech article I linked he says that all controller manufacturers announced TRIM support by end of the year. It&#8217;s not there yet. And if you can&#8217;t update the firmware this is all moot anyway.

---

### Post by josephellengar on 2009-09-27
> **hugmenot said:**
> In the month-old Anandtech article I linked he says that all controller manufacturers announced TRIM support by end of the year. It’s not there yet. And if you can’t update the firmware this is all moot anyway.

But he also says that a number of drives do have support, notably the indilinx drives.  And the intel g2 drives have complete support, so IMO koala should implement OS level support.

---

### Post by hugmenot on 2009-09-27
> **idigchess said:**
> But he also says that a number of drives do have support, notably the indilinx drives.  And the intel g2 drives have complete support, so IMO koala should implement OS level support.

Maybe you&#8217;re right. I was under the impression that the Indilinx version of TRIM was not the finalized ATA version, which is why he had to use this wiper tool. But I only read diagonally to find what I was after.

Anyhow, I doubt it will be enabled, even if possible. It&#8217;s too close to release for something scary like this to be enabled. Ext4 is new, trim is new, no testing possible. It would make for a magnificent desaster if a  bug makes it into release. Don&#8217;t trash user data must be a maxim that trumps all performance concerns.

---

### Post by josephellengar on 2009-09-27
> **hugmenot said:**
> Maybe your right. I was under the impression that the Indilinx version of TRIM was not the finalized ATA version, which is why he had to use this wiper tool. But I only read diagonally to find what I was after.

I think so.  But I'm sure that g2 drives fully support it.  That was one of the reasons why they only really had to update the controller to get g2, rather than the actual memory chips.

---

### Post by andrewabc on 2009-09-28
Indilinx drives do support TRIM, OCZ and others had released beta drives with TRIM working, but there were other problems so they are still developing the firmware (complete rewrite). Which I think it is safe to assume will be released by end of October at latest.

So I hope to see a kernel update that turns on TRIM at some point. From what I read it is disabled, and can be enabled in future once SSD support it(?).

---

### Post by nhasian on 2009-09-28
I found [this]("http://www.cdfreaks.com/review/19929-intel-x25-m-ssd-review/Drive-specifications-and-features-2/") article posted two weeks ago.

> 
ATA TRIM as an extension of the ATA command set. ATA TRIM basically checks the file allocation table on the drive for deleted files. Then it reorders and erases blocks on the drive. The down side to ATA TRIM is that it is operating system dependent, and currently, only Windows 7 and the latest distributions of Linux with the ext4 file system will support ATA TRIM.

ATA TRIM also requires the complete ATA stack to support TRIM and SSD controller to support the TRIM command. TRIM is not supported in the G1 series of Intel X25-M SSD.

So I guess the 2nd Gen Intel SSD Drives do support ATA-TRIM.

---

### Post by josephellengar on 2009-09-28
> **nhasian said:**
> I found [this]("http://www.cdfreaks.com/review/19929-intel-x25-m-ssd-review/Drive-specifications-and-features-2/") article posted two weeks ago.



So I guess the 2nd Gen Intel SSD Drives do support ATA-TRIM.

Yeah, so what's the consensus?  Will karmic have it in effect?

---

### Post by andrewabc on 2009-09-28
> **nhasian said:**
> I found [this]("http://www.cdfreaks.com/review/19929-intel-x25-m-ssd-review/Drive-specifications-and-features-2/") article posted two weeks ago.

So I guess the 2nd Gen Intel SSD Drives do support ATA-TRIM.

Yes, I think most already know that TRIM won't work unless SSD firmware supports it. The question everyone has been asking is will TRIM work out of the box with ubuntu assuming SSD has TRIM firmware?

Yes we know the kernel has TRIM support. But will it work without having to mess around with stuff? Can I install Ubuntu 9.10 final (October 31) to an SSD with TRIM firmware and ubuntu will know it is an SSD and possibly properly align it, and automatically do TRIM?

@idigchess I'm as frustrated as you :P Might as well assume that neither will happen, and that it will all have to be manually done somehow. Hopefully some good guides are put up for SSD users.

---

### Post by MellonCollie on 2009-09-29
> **idigchess said:**
> Trim needs to be implemented at the OS level, not just at the kernel level.

Ahh, I see. ](*,)

---

### Post by MacUntu on 2009-09-29
So I guess the conclusion is: no, Karmic will not have out-of-box SSD support. Of course it will run (faster than your HDD) but there won't be special optimizations (TRIM, partition alignment).

---

### Post by antiram on 2009-09-29
> **andrewabc said:**
> 
Yes we know the kernel has TRIM support. But will it work without having to mess around with stuff? Can I install Ubuntu 9.10 final (October 31) to an SSD with TRIM firmware and ubuntu will know it is an SSD and possibly properly align it, and automatically do TRIM?

kernel TRIM support is not completed and doesnt work. CFQ io-scheduler have optimized settings for SSDs, which are used if the SSDs reports rotating speed ~0. eg. my indilinx with 1711 firmware reports with hdparm:
Nominal Media Rotation Rate: Solid State Device
*	Data Set Management TRIM supported

there is a TRIM solution called wiper.sh in new hdparm packages:
[http://sourceforge.net/projects/hdparm/](http://sourceforge.net/projects/hdparm/)
[http://www.ocztechnologyforum.com/forum/showthread.php?t=60882](http://www.ocztechnologyforum.com/forum/showthread.php?t=60882)

---

### Post by hugmenot on 2009-09-30
Ok. I completely wiped my SSD with SECURE ERASE. Here are the numbers:

[benchmark: dbench -s2]("http://article.gmane.org/gmane.linux.suse.opensuse.devel/23070")
```
Baseline: (disk 75% filled; ~4 months of quite heavy usage)

Unaligned, unqualified      10.3867 MB/sec max_latency=243.054 ms
Unaligned, stripe-width=128 10.2559 MB/sec max_latency=248.230 ms
Aligned, unqualified        11.9774 MB/sec max_latency=233.829 ms
Aligned, stripe-width=128   11.9539 MB/sec max_latency=177.437 ms

Post ATA SECURE ERASE:

Unaligned, unqualified      10.2698 MB/sec max_latency=111.910 ms
Unaligned, stripe-width=128  9.8834 MB/sec max_latency=105.029 ms
Aligned, unqualified        10.9740 MB/sec max_latency=130.026 ms
Aligned, stripe-width=128   11.1741 MB/sec max_latency=94.548 ms

Post ATA ENHANCED SECURE ERASE:

Unaligned, stripe-width=128   27.7824 MB/sec max_latency=79.726 ms
Aligned, stripe-width=128     48.6741 MB/sec max_latency=62.098 ms
```


Even though I was fed up with benchmarking I ran the last one twice. I just didn&#8217;t trust these numbers. I still find them astonishing. But anyway, this took a while. Especially the fumbling with sfdisk and fdisk, etc.

Not TRIM, but there is a very definite improvement. Things like aptitude, make, etc, all that writes small files is much faster now.

---

### Post by slight on 2009-10-24
I'm pretty sure after some research that the following is correct, YMMV.

The second gen X25 drives do not yet support real trim in the firmware. Intel have said there'll be a firmware update to enable it before the end of the year. They won't be releasing an update to enable trim for the G1 apparently even though they could. However the G2 already have excellent 'used' performance that the other providers can't provide except the Indilinx 'pseudo-trim'.

Currently no drives support real trim in firmware. As someone said the Indilinx based drives had a beta driver with support but it trashed data when the computer was put into sleep so they pulled it.

There is a sort of offline trim available at least for the Indilinx drives where it does one big trim across the whole drive, which is useful, but it's not the same as the os/filesystem level trim reporting that'll be coming in future firmware updates.

---

### Post by andrewabc on 2009-10-24
> **slight said:**
> 
Currently no drives support real trim in firmware. As someone said the Indilinx based drives had a beta driver with support but it trashed data when the computer was put into sleep so they pulled it.


OCZ and I presume all Indilinx drives support TRIM.
OCZ released new firmware October 13 that enables TRIM. They also released firmware with good garbage collection for OS that do not support TRIM.

[AGILTY and VERTEX FW update 1.4/1.41... VERTEX EX and AGILITY EX FW 1.3/1.31 EX ](http://www.ocztechnologyforum.com/forum/showthread.php?t=63498)
1.40 is TRIM firmware
1.41 is garbage collection (GC) firmware.

I plan on upgrading my 60gb vertex to GC firmware before I format and install ubuntu 9.10 so probably very early November. The firmware upgrade is non destructive.

---

### Post by nhasian on 2009-10-26
It's [COLOR="Blue"]official[/COLOR] now.  2nd Gen Intel drives have TRIM enabled in their latest firmware:

[http://www.tcmagazine.com/comments.php?id=30487&catid=3](http://www.tcmagazine.com/comments.php?id=30487&catid=3)

---

### Post by shailesh on 2009-10-26
Does the fact that it's "Complete" in the Release Status mean that TRIM is working on the OS level? 

Check it out: [https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Karmic](https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Karmic)

Under the kernel-karmic-ssd

---

### Post by andrewabc on 2009-10-26
Odd that it says complete (I think just research/recommendations). But I'm 100% certain that TRIM does not 'auto' work if installing karmic to SSD. The TRIM kernel developer has stated so.

[The truth about firmware 1.4 and Linux](http://www.ocztechnologyforum.com/forum/showthread.php?t=63843) (first poster is misinformed).

mlord is the developer.

I would not count on it. But I would definitely expect it in 10.04

For OCZ vertex 512kb is best alignment. Maybe they will adjust the 128kb suggestion. Although the most important part is that it is multiples of 64kb which 128 and 512 are. You want aligned to the [erase block](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226).

---

### Post by tnttrx on 2009-10-26
TRIM firmwares for both Intel and Indilinx controlers are out:
[http://www.anandtech.com/storage/showdoc.aspx?i=3667&p=1](http://www.anandtech.com/storage/showdoc.aspx?i=3667&p=1)

Performace difference is huge in used-ssd scenario:
> 4KB Random Write, IOQ=16 	=>  Run 1 	=>  Run 2 after Deleting Partition
Intel X25-M 80GB TRIM Firmware 	=>  37.9 MB/s 	=>  17.9 MB/s

All work needed to be done is to send TRIM command to SSD once filesystem deleted some files. Ofcorse, TRIM should be followed with LBAs not in use any more. That way SSD has more space on it's disposal, affecting both performance and wear leveling. 

Very important thing to have, no doubt!

btw, I would go for complete erase block alignment:
[http://anandtech.com/storage/showdoc.aspx?i=3631&p=3](http://anandtech.com/storage/showdoc.aspx?i=3631&p=3)

---

### Post by andrewabc on 2009-10-26
> **tnttrx said:**
> 
btw, I would go for complete erase block alignment:
[http://anandtech.com/storage/showdoc.aspx?i=3631&p=3](http://anandtech.com/storage/showdoc.aspx?i=3631&p=3)

Which for ocz vertex is 512kb which is what I stated in my previous post, and in your link.
Although the article you linked states that for higher 4kb random, you want 4kb alignment. Which I don't think anyone recommends. If you go with 512kb alignment, adn write 4kb file, the entire 512 will be rewritten. Better for larger files, worse for smaller.

Although I completely understand if the OS could auto determine this for each SSD and appropriately automatically align properly.

OCZ new firmware was out October 13.

---

### Post by josephellengar on 2009-10-26
> **andrewabc said:**
> Which for ocz vertex is 512kb which is what I stated in my previous post, and in your link.
Although the article you linked states that for higher 4kb random, you want 4kb alignment. Which I don't think anyone recommends. If you go with 512kb alignment, adn write 4kb file, the entire 512 will be rewritten. Better for larger files, worse for smaller.

Although I completely understand if the OS could auto determine this for each SSD and appropriately automatically align properly.

OCZ new firmware was out October 13.

So we don't have trim in Karmic?  Should I still buy an SSD?  And if I do a clean install of Windows (which automatically aligns) and then install Ubuntu next to it, will the two fs remain aligned?  Is there that much of a performance degradation if I don't really care about the write amplification (I definitely don't write enough data to kill the thing before the warranty ends)?

---

### Post by tnttrx on 2009-10-26
alignment to 512KB will satisfy 4KB-alignment, too.
I would go for 512KB.

@idigchess
SSD will still be much faster then hard drive, and once TRIM is implemented in Ubuntu, you will benefit as it will speedup (TRIM) your already used SSD.
go for SSD, but watch what you buy: Intel **G2** or Indilinx based OCZ (**Vertex**, **Agility**) or Patriot (**Troqx**).

---

### Post by josephellengar on 2009-10-26
> **tnttrx said:**
> alignment to 512KB will satisfy 4KB-alignment, too.
I would go for 512KB.

@idigchess
SSD will still be much faster then hard drive, and once TRIM is implemented in Ubuntu, you will benefit as it will speedup (TRIM) your already used SSD.
go for SSD, but watch what you buy: Intel **G2** or Indilinx based OCZ (**Vertex**, **Agility**) or Patriot (**Troqx**).

Yeah, I found the Intel G2 160 for only 470 dollars.  Awesome.  How would I go about aligning it though?  And is it worth the effort?  Oh, and I know that my W7 partition will automatically trim itself, but would the trim script (wiper.sh) work equally well for the ubuntu partition, since it probably won't be until next release that trim is implemented?  Thanks!

---

### Post by apocalypse80 on 2009-10-26
> **idigchess said:**
> And if I do a clean install of Windows (which automatically aligns) and then install Ubuntu next to it, will the two fs remain aligned?

I partitioned with win7, then formatted some partitions with ext4 (via live cd).
They remain aligned.

I went through the new-used-trimmed(=new) cycle and honestly in real-life apps I see no difference whatsoever.
I needed synthetic benchmarks to notice the degradation after use and the improvement from trim.
But I guess that might be different for different ssds.

Oh and trim or no trim, small file performance is *dramatically* better with ubuntu/ext4 than it is under win7/ntfs.

---

### Post by tnttrx on 2009-10-26
> **apocalypse80 said:**
> I went through the new-used-trimmed(=new) cycle and honestly in real-life apps I see no difference whatsoever.

everything depends on how hard you used SSD before triming. 

anyway, how did you trim it?

---

### Post by apocalypse80 on 2009-10-26
> **tnttrx said:**
> everything depends on how hard you used SSD before triming. 

anyway, how did you trim it?

Windows 7, with the intel ssd tool - just a few hours ago.
It's seen some use, including lots of benchmarks, 1.6TB of total writes according to the Intel tool

---

### Post by tnttrx on 2009-10-26
> **apocalypse80 said:**
> Windows 7, with the intel ssd tool - just a few hours ago.
It's seen some use, including lots of benchmarks, 1.6TB of total writes according to the Intel tool

well, here I'm not sure, but you should check if Intel Tool can affect ext4 partition.

afaik, wiper tools like Intel Tool ask filesystem to list all files and their location and then feed SSD with all other locations (as free). that way SSD deletes all unused parts of filesystem from it's own "used blocks table".

if Intel Tool can "communicate" with ext4 just as well as with ntfs, it will work. but, I'm afraid that Intel just cares about m$ users and will not try to implement anything for ext4.

:(

---

### Post by Penguin Guy on 2009-10-26
> **idigchess said:**
> Trim needs to be implemented at the OS level, not just at the kernel level.
Are you sure?

---

### Post by apocalypse80 on 2009-10-26
> **tnttrx said:**
> if Intel Tool can "communicate" with ext4 just as well as with ntfs, it will work. but, I'm afraid that Intel just cares about m$ users and will not try to implement anything for ext4.

Bingo.
It lists my ntfs and fat32 partitions, but nothing about the ext4 ones or swap.

---

### Post by tnttrx on 2009-10-26
Intel Tool just has no way to determine which block doesn't contain valid data any more, except if list of all valid data is supplied by filesystem.

---

### Post by josephellengar on 2009-10-26
> **tnttrx said:**
> well, here I'm not sure, but you should check if Intel Tool can affect ext4 partition.

afaik, wiper tools like Intel Tool ask filesystem to list all files and their location and then feed SSD with all other locations (as free). that way SSD deletes all unused parts of filesystem from it's own "used blocks table".

if Intel Tool can "communicate" with ext4 just as well as with ntfs, it will work. but, I'm afraid that Intel just cares about m$ users and will not try to implement anything for ext4.

:(

Can the wiper.sh tool that people use within ubuntu wipe ntfs partitions?  That might be a good way to get the entire fs trimmed.

---

### Post by andrewabc on 2009-10-26
> **idigchess said:**
> So we don't have trim in Karmic?  Should I still buy an SSD?  And if I do a clean install of Windows (which automatically aligns) and then install Ubuntu next to it, will the two fs remain aligned?  Is there that much of a performance degradation if I don't really care about the write amplification (I definitely don't write enough data to kill the thing before the warranty ends)?

No TRIM in karmic unless you download and run separate program (still not really recommended yet).

You can align an SSD from ubuntu livecd (or another hard drive). Dunno about windows/linux combos on same SSD.

You probably won't notice a lot of speed loss by not aligning.

Read
[Linux - Tips, tweaks and alignment](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379).

If you buy OCZ vertex/agility, you can get firmware with garbage collection which speeds up SSD (similar to TRIM). This works on all OS and it is the SSD that does the work in the background. Basically it is being recommended for everyone except those running win7 (as it is the only one that supports TRIM).

---

### Post by josephellengar on 2009-10-26
> **andrewabc said:**
> No TRIM in karmic unless you download and run separate program (still not really recommended yet).

You can align an SSD from ubuntu livecd (or another hard drive). Dunno about windows/linux combos on same SSD.

You probably won't notice a lot of speed loss by not aligning.

Read
[Linux - Tips, tweaks and alignment](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379).

If you buy OCZ vertex/agility, you can get firmware with garbage collection which speeds up SSD (similar to TRIM). This works on all OS and it is the SSD that does the work in the background. Basically it is being recommended for everyone except those running win7 (as it is the only one that supports TRIM).

Seems like a lot of work for the alignment.  Is it worth it.  Also, what about the wiper.sh tool?  If I use that instead of indilinx garbage collection are the results the same?  It seemed to me like they would be, but I am by no means an expert on the topic.  I just wanted to go with an intel drive based on my research, and those don't have the garbage collection so I'd have to use wiper.

---

### Post by andrewabc on 2009-10-26
> **idigchess said:**
> Seems like a lot of work for the alignment.  Is it worth it.  Also, what about the wiper.sh tool?  If I use that instead of indilinx garbage collection are the results the same?  It seemed to me like they would be, but I am by no means an expert on the topic.  I just wanted to go with an intel drive based on my research, and those don't have the garbage collection so I'd have to use wiper.

I think alignment by the time I read the guides, and carefully making sure I was doing it correctly, and got it done took 30 minutes. Not as long as it looks. I havn't done any other tweaks other than almost turning off swap. I'm running ubuntu 9.04, so no need to do anything until 9.10 installed (waste of time doing it to 9.04 if only having it installed fr another week).

Yah, the linux program (TRIM) and garbage collection should give similar speed increases (I have no idea, but really they should based upon OCZ TRIM vs GC firmware). Hopefully for 10.04 ubuntu has TRIM enabled by default, so you'll only have to deal with it for 6 months.

I was going to get a 80gb intel but the price didn't come down fast enough and a 60gb vertex went on sale for $200 CAD free shipping (meanwhile 80gb intel is currently $300 CAD + shipping).

---

### Post by josephellengar on 2009-10-26
> **andrewabc said:**
> I think alignment by the time I read the guides, and carefully making sure I was doing it correctly, and got it done took 30 minutes. Not as long as it looks. I havn't done any other tweaks other than almost turning off swap. I'm running ubuntu 9.04, so no need to do anything until 9.10 installed (waste of time doing it to 9.04 if only having it installed fr another week).

Yah, the linux program (TRIM) and garbage collection should give similar speed increases (I have no idea, but really they should based upon OCZ TRIM vs GC firmware). Hopefully for 10.04 ubuntu has TRIM enabled by default, so you'll only have to deal with it for 6 months.

I was going to get a 80gb intel but the price didn't come down fast enough and a 60gb vertex went on sale for $200 CAD free shipping (meanwhile 80gb intel is currently $300 CAD + shipping).

So, if I just start the partition 2048 sectors from the disk boundary would that be enough?  I could do that in gparted, right?

---

### Post by andrewabc on 2009-10-26
> **idigchess said:**
> So, if I just start the partition 2048 sectors from the disk boundary would that be enough?  I could do that in gparted, right?

You first align the disk using instructions [here](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226). I'm not 100% certain if would work for intel 80gb, or is more specific for OCZ vertex. I'd assume it is very similar.

Then you go into gparted and create your partitions (linux / and say swap).

At least that is how I remember it. I aligned before doing anything else, then created partitions and installed from livecd. As far as I know it worked fine.

---

### Post by josephellengar on 2009-10-27
> **andrewabc said:**
> You first align the disk using instructions [here](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226). I'm not 100% certain if would work for intel 80gb, or is more specific for OCZ vertex. I'd assume it is very similar.

Then you go into gparted and create your partitions (linux / and say swap).

At least that is how I remember it. I aligned before doing anything else, then created partitions and installed from livecd. As far as I know it worked fine.

But is it worth the effort?  I've heard that alignment really doesn't give much performance benefit, that it just reduces the write amplification.

---

### Post by apocalypse80 on 2009-10-27
> **idigchess said:**
> But is it worth the effort?  I've heard that alignment really doesn't give much performance benefit, that it just reduces the write amplification.

According to synthetics (like crystaldiskmark) I gained quite a bit in terms of small random writes - to the tune of +50%.
But even if it was less, there's no way I'd allow a 400 euro piece of kit operate at anything under maximum efficiency.

And I will repeat, you can create a perfect alignment by creating ALL partitions with win7 and the alignment will remain after you format some partitions with ext4.
This method requires 0 effort.

---

### Post by josephellengar on 2009-10-27
> **apocalypse80 said:**
> According to synthetics (like crystaldiskmark) I gained quite a bit in terms of small random writes - to the tune of +50%.
But even if it was less, there's no way I'd allow a 400 euro piece of kit operate at anything under maximum efficiency.

And I will repeat, you can create a perfect alignment by creating ALL partitions with win7 and the alignment will remain after you format some partitions with ext4.
This method requires 0 effort.

Okay, I misread your previous posts.  You mean if I make several all three of my necessary partitions into ntfs using the Win7 partition tool and then reformat them, they will all automatically be aligned?  If so, where do I find the win7 partition tool?  I'm not that familiar with Vista/7 but I'm going to install it as soon as I get my new comp.  (1 week!)

---

### Post by apocalypse80 on 2009-10-27
> **idigchess said:**
> Okay, I misread your previous posts.  You mean if I make several all three of my necessary partitions into ntfs using the Win7 partition tool and then reformat them, they will all automatically be aligned?

Yes.
Except you can just leave linux partitions unformatted initially.

> If so, where do I find the win7 partition tool?  I'm not that familiar with Vista/7 but I'm going to install it as soon as I get my new comp.  (1 week!)

It comes with the OS, it's the normal disk management tool (control panel -> administrative tools).
I just connected the ssd to a pc already running 7 as a secondary drive.
The win7 installation process also creates aligned partitions, but it lacks any options.

---

### Post by tnttrx on 2009-10-27
seems like win7 is fully aware of non-rotating drives. 

good thing to know (and make use of it :) ).

---

### Post by tnttrx on 2009-10-27
**!!! ATTENTION !!!**


beware of:
[http://www.dailytech.com/article.aspx?newsid=16638](http://www.dailytech.com/article.aspx?newsid=16638)

:evil:

---

### Post by josephellengar on 2009-10-27
> **tnttrx said:**
> **!!! ATTENTION !!!**


beware of:
[http://www.dailytech.com/article.aspx?newsid=16638](http://www.dailytech.com/article.aspx?newsid=16638)

:evil:

LOL!  I was entering my credit card info for the order when the email popped up!  Thank you so much! :oops:

---

### Post by tnttrx on 2009-10-28
sorry to ruin your upgrade.

either wait for proven Intel firmware or go for OCZ:

the greatest Intel advantage over Indilinx-based SSDs is 4KB random writes.

honestly, I don't think any linux desktop user will see a lot of 4KB random writes unless he/she uses "noop" scheduler and/or disables write buffering.

---

### Post by josephellengar on 2009-10-28
> **tnttrx said:**
> sorry to ruin your upgrade.

either wait for proven Intel firmware or go for OCZ:

the greatest Intel advantage over Indilinx-based SSDs is 4KB random writes.

honestly, I don't think any linux desktop user will see a lot of 4KB random writes unless he/she uses "noop" scheduler and/or disables write buffering.

Which one?  OCZ vertex 120gb?  I was looking at that but I thought that the used performance didn't look great compared to the intel drives and we still don't know if trim will really work all that great.  Is the trim support in thos drives stable?  I need 100gb, so I can't really go with anything smaller.

---

### Post by andrewabc on 2009-10-28
> **idigchess said:**
> Which one?  OCZ vertex 120gb?  I was looking at that but I thought that the used performance didn't look great compared to the intel drives and we still don't know if trim will really work all that great.  Is the trim support in thos drives stable?  I need 100gb, so I can't really go with anything smaller.

Read the threads at OCZ forum (two SSD sections). Lots of people give benchmarks.
[http://www.ocztechnologyforum.com/forum/index.php](http://www.ocztechnologyforum.com/forum/index.php)

I don't think used performance is a big problem, maybe intel used is better I dunno. Pretty sure recent anandtech article did benchmarks. TRIM and garbage collection is supposed to take care of that. You should end up with 90% new speed. Anandtech recommends 20% drive free space for optimal speed (and probably wear leveling).

With OCZ you can use TRIM or Garbage collection firmware. Since TRIM only works on win7, if running linux you'd want garbage collection firmware until linux support improves.

TRIM on OCZ is stable as far as I know. But linux doesn't support TRIM fully yet, so you'd be better off with GC firmare until ubuntu 10.04 release (unless TRIM for linux stabilizes a lot).

Demand is high, supply low for SSD, so they are still expensive (similar prices as March 2009). You pretty much have to wait for a big sale for a decent price.

Check out OCZ vertex 120gb price history at newegg
[http://diskcompare.com/disk/666/](http://diskcompare.com/disk/666/)  (graph on left side)
The new firmwares (TRIM) out for SSD have caused demand increase.

Intel prices are no better. Still ~$60 above suggested price from 3 months ago...

---

### Post by antiram on 2009-10-28
trim works on linux, use wiper.sh every day. Where is the problem? 

Make a daily cronjob for wiper.sh (and comment out line 511-517 in wiper-2.5 for the "do you really want..") 
as /etc/cron.daily/wiper:
```
#!/bin/sh

test -x /usr/local/bin/wiper.sh || exit 0
date >> /var/log/wiper.log
/usr/local/bin/wiper.sh --commit / >>/var/log/wiper.log
/usr/local/bin/wiper.sh --commit /home >>/var/log/wiper.log

```

w7/vista is not needed for partitioning. Use "fdisk -H32 -S32 /dev/sda" for 512k alignment or use "fdisk -u" to set the sector numbers like men, like real men!!!

used performance after wiper with Supertalent Ultradrive 128GB Firmware 1819
```
root@locutus:~# iozone -I -a -s 256M -r 4k -r 64k -r 512k -i 0 -i 1 -i 2
	Iozone: Performance Test of File I/O
	        Version $Revision: 3.308 $
		Compiled for 64 bit mode.
		Build: linux 

	Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
	             Al Slater, Scott Rhine, Mike Wisner, Ken Goss
	             Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
	             Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
	             Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy,
	             Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root.

	Run began: Thu Oct 29 00:42:25 2009

	O_DIRECT feature enabled
	Auto Mode
	File size set to 262144 KB
	Record Size 4 KB
	Record Size 64 KB
	Record Size 512 KB
	Command line used: iozone -I -a -s 256M -r 4k -r 64k -r 512k -i 0 -i 1 -i 2
	Output is in Kbytes/sec
	Time Resolution = 0.000001 seconds.
	Processor cache size set to 1024 Kbytes.
	Processor cache line size set to 32 bytes.
	File stride size set to 17 * record size.
                                                            random  random    bkwd   record   stride                                   
              KB  reclen   write rewrite    read    reread    read   write    read  rewrite     read   fwrite frewrite   fread  freread
          262144       4   52588   59931    49144    49201   29894   15370                                                          
          262144      64  115506  122981   229070   229314  133219  129767                                                          
          262144     512  145350  140268   259870   260296  216764  146239                                                          

iozone test complete.

```

---

### Post by josephellengar on 2009-10-28
> **antiram said:**
> trim works on linux, use wiper.sh every day. Where is the problem? 

Make a daily cronjob for wiper.sh (and comment out line 511-517 in wiper-2.5 for the "do you really want..") 
as /etc/cron.daily/wiper:
```
#!/bin/sh

test -x /usr/local/bin/wiper.sh || exit 0
date >> /var/log/wiper.log
/usr/local/bin/wiper.sh --commit / >>/var/log/wiper.log
/usr/local/bin/wiper.sh --commit /home >>/var/log/wiper.log

```

w7/vista is not needed for partitioning. Use "fdisk -H32 -S32 /dev/sda" for 512k alignment or use "fdisk -u" to set the sector numbers like men, like real men!!!

used performance after wiper with Supertalent Ultradrive 128GB Firmware 1819
```
root@locutus:~# iozone -I -a -s 256M -r 4k -r 64k -r 512k -i 0 -i 1 -i 2
	Iozone: Performance Test of File I/O
	        Version $Revision: 3.308 $
		Compiled for 64 bit mode.
		Build: linux 

	Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
	             Al Slater, Scott Rhine, Mike Wisner, Ken Goss
	             Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
	             Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
	             Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy,
	             Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root.

	Run began: Thu Oct 29 00:42:25 2009

	O_DIRECT feature enabled
	Auto Mode
	File size set to 262144 KB
	Record Size 4 KB
	Record Size 64 KB
	Record Size 512 KB
	Command line used: iozone -I -a -s 256M -r 4k -r 64k -r 512k -i 0 -i 1 -i 2
	Output is in Kbytes/sec
	Time Resolution = 0.000001 seconds.
	Processor cache size set to 1024 Kbytes.
	Processor cache line size set to 32 bytes.
	File stride size set to 17 * record size.
                                                            random  random    bkwd   record   stride                                   
              KB  reclen   write rewrite    read    reread    read   write    read  rewrite     read   fwrite frewrite   fread  freread
          262144       4   52588   59931    49144    49201   29894   15370                                                          
          262144      64  115506  122981   229070   229314  133219  129767                                                          
          262144     512  145350  140268   259870   260296  216764  146239                                                          

iozone test complete.

```

Real trim would be automatic, OS based, without needing a script to manually do it.  And if the tool works, it works.  It doesn't matter how it's done.

---

### Post by tnttrx on 2009-10-28
@antiram

great performance indeed!

---

### Post by josephellengar on 2009-10-29
> **andrewabc said:**
> Read the threads at OCZ forum (two SSD sections). Lots of people give benchmarks.
[http://www.ocztechnologyforum.com/forum/index.php](http://www.ocztechnologyforum.com/forum/index.php)

I don't think used performance is a big problem, maybe intel used is better I dunno. Pretty sure recent anandtech article did benchmarks. TRIM and garbage collection is supposed to take care of that. You should end up with 90% new speed. Anandtech recommends 20% drive free space for optimal speed (and probably wear leveling).

With OCZ you can use TRIM or Garbage collection firmware. Since TRIM only works on win7, if running linux you'd want garbage collection firmware until linux support improves.

TRIM on OCZ is stable as far as I know. But linux doesn't support TRIM fully yet, so you'd be better off with GC firmare until ubuntu 10.04 release (unless TRIM for linux stabilizes a lot).

Demand is high, supply low for SSD, so they are still expensive (similar prices as March 2009). You pretty much have to wait for a big sale for a decent price.

Check out OCZ vertex 120gb price history at newegg
[http://diskcompare.com/disk/666/](http://diskcompare.com/disk/666/)  (graph on left side)
The new firmwares (TRIM) out for SSD have caused demand increase.

Intel prices are no better. Still ~$60 above suggested price from 3 months ago...

correct me if I'm wrong, but I didn't think that the OCZ garbage collecting firmware worked on non-NTFS partitions.

---

### Post by antiram on 2009-10-29
garbage collection has nothing to do with ntfs. gc is needed on every ssd with write combining = log structured (eg. indilinx, intel).
[http://lwn.net/Articles/353411/](http://lwn.net/Articles/353411/)

it is only the question how much garbage must be cleaned. Most garbage cleaning means heavy writing and wear out for good performance without trim. The ssd lives longer with trim.

---

### Post by josephellengar on 2009-10-29
> **antiram said:**
> garbage collection has nothing to do with ntfs. gc is needed on every ssd with write combining = log structured (eg. indilinx, intel).
[http://lwn.net/Articles/353411/](http://lwn.net/Articles/353411/)

it is only the question how much garbage must be cleaned. Most garbage cleaning means heavy writing and wear out for good performance without trim. The ssd lives longer with trim.

Okay, I think I might not get this.  I thought that garbage collecting was an indilinx-specific firmware algorithm that allowed the ssd to figure out which files had been deleted and remove them, similar to trim, when the computer was idle for 2+ hours, completely independent of the OS.  I was pretty sure that Intel had nothing of the like. 

Yeah, based on this article: 
[http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=14](http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=14)
it appears that only samsung and indilinx have this right now.  So I don't think that it's needed on every ssd with write combining.  But anyway, I still am pretty sure that the indilinx one can't work on an ext4 fs.

---

### Post by antiram on 2009-10-29
the ntfs feature has only samsung. anand talks about a "cleaning lady" 
[http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=4](http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=4)
which is the garbage collection as basic technical necessity.

---

### Post by josephellengar on 2009-10-29
> **antiram said:**
> the ntfs feature has only samsung. anand talks about a "cleaning lady" 
[http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=4](http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=4)
which is the garbage collection as basic technical necessity.

Okay, we're talking about different things.  What I was talking about was the idle garbage collection, not the cleaning lady.  As here, it is not necessary because only Indilinx and samsung have it right now, but not Intel.  And, at least for samsung (probably Indi) it only works on NTFS.

> 

Impact of Idle Garbage Collection

The other option that Indilinx provides its users to improve used performance is something called idle or background garbage collection. The idea is that without any effort on your or the OS’ part your drive, while idle, will defragment itself.

The feature was actually first introduced by Samsung for its RBB based drives, but I’ll get to the issues with Samsung’s drives momentarily.

It either works by looking at the data on the drive and organizing it into a less fragmented state, or by looking at the file system on the drive and attempting to TRIM based on what it finds. Both Indilinx and Samsung have attempted to implement this sort of idle garbage collection and it appears they do it in different ways. While the end result is the same, how they get there determines the usefulness of this feature.

In the first scenario, this is not simply TRIMing the contents of the drive, the drive doesn’t know what to TRIM; it must still keep track of all data. Instead, the drive is re-organizing its data to maximize performance.

The second scenario requires a compatible file system (allegedly NTFS for the Samsung drives) and then the data is actually TRIMed as it would be with the TRIM instruction.

Details are slim, but the idle garbage collection does work in improving performance:
PCMark Vantage HDD Score 	New 	"Used" 	After TRIM/Idle GC 	% of New Perf
Corsair P256 (Samsung MLC) 	26607 	18786 	24317 	91%

 

Presumably this isn’t without some impact to battery life in a notebook. Furthermore, it’s impossible to tell what impact this has on the lifespan of the drive. If a drive is simply reorganizing data on the fly into a better (higher performing) state, that’s a lot of reads and writes when you’re doing nothing at all. And unfortunately, there’s no way to switch it off.

While Indilinx is following in Samsung's footsteps with enabling idle garbage collection, I believe it's a mistake. Personally, real TRIM support (or at least the wiper tool) is the way to go and it sounds like we’ll be getting it for most if not all of these SSDs in the next couple of months. Idle garbage collection worries me.

Citations: [http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=14](http://www.anandtech.com/storage/showdoc.aspx?i=3631&p=14)

---

### Post by andrewabc on 2009-10-29
I'm 100% certain that Garbage collection will work on non NTFS. It will work on ext4. GC has nothing to do with filesystem or operating system.

Also garbage collection starts working within minutes. You no longer have to put computer idle for several hours (although it will allow GC to work better and more thorough eg. you fill, then empty the drive several times).

[What settings do I need to make garbage collection work?](http://www.ocztechnologyforum.com/forum/showthread.php?t=62830)

There are several threads at OCZ forum about this.
GC works automatically, and on any filesystem or OS.

[GC goes to 95% performance in 1 hour](http://www.ocztechnologyforum.com/forum/showpost.php?p=445153&postcount=6)

So either the people working at OCZ are complete liars and no one bothered to refute their claims (there is a kernel developer there...), or it does what they say.

---

### Post by apocalypse80 on 2009-10-31
To answer the original question, no karmic doesn't have trim in effect.

However I grew a pair and tried wiper.sh (from hdparm 9.27) - it definitely works for intel drives too.

this

```
########################################################################
X25-M UNTRIMMED iozone
########################################################################

                                                  random  random
    KB  reclen   write rewrite    read    reread    read   write
262144       4   55854   61601    77975    77408   18740   37199
262144       8   79397   74942   107490   107615   34600   39998
262144      16   92717   81941   147162   147530   60921   45298
262144      32   98133   86319   175378   175948   98278   49321
262144      64  102575   87223   200613   201029  141870   70205
262144     128   96168  100709   224931   223912  181481   79198
262144     256   95011  103151   233538   234261  212879   73557
262144     512  110951   93840   244588   242498  233184   95013
262144    1024  112000   94834   253001   248172  245917   76849
262144    2048  112031   95471   252609   250570  209723   69661
262144    4096   98865  107274   255614   255558  213758   75851
262144    8192   97032   93397   258498   258156  238280  111814
```

turned into this

```
########################################################################
X25-M TRIMMED iozone
########################################################################

                                                  random  random
    KB  reclen   write rewrite    read    reread    read   write
262144       4   55436   65711    79852    80149   19067   53292
262144       8   77232   84058   109771   110180   34861   78440
262144      16   88799   94750   149140   147288   61525   94093
262144      32   97577  101654   174621   171067   98781  100264
262144      64  101396  106724   197531   202331  143772  106063
262144     128  107555  106179   220295   218789  180567  109024
262144     256  109005  108426   231249   226626  211819  110158
262144     512  107378  110893   233207   235219  233527  109245
262144    1024  110281  111575   241247   240927  244339  111624
262144    2048  111814  112242   242394   243583  208330  110694
262144    4096  110209  112247   248230   248664  213787  112301
262144    8192  111614  112405   250563   250567  238135  112355
```

You gotta love intel's capped write speed...
The process is as fast as the intel tool under windows (a couple of seconds) and I guess it could be automated with cron if one edits out the verification questions.
It doesn't work on ntfs however, it only trimmed my ext4 partitions.

It really isn't that bad considering that only win7 users get auto trim.
Under vista and xp you need to use tools exactly like this.

---

### Post by runesvend on 2009-12-06
I just ran the wiper script on my 80GB X-25M Postville as well. Results:

```
BEFORE:

	Output is in Kbytes/sec
                                                            random  random
              KB  reclen   write rewrite    read    reread    read   write
          262144       4   32925   40142    44519    43749   17835    8443
          262144      64   81012   82615   199672   199854  140188   20138
          262144     512   34904   83236   249276   248545  227652   39838

AFTER:

	Output is in Kbytes/sec
                                                            random  random
              KB  reclen   write rewrite    read    reread    read   write
          262144       4   36490   40840    44292    44289   17956   37066
          262144      64   80661   81554   200097   198793  141341   80823
          262144     512   83239   59139   247916   248620  232914   80520
```

It seems that only the write performance is affected. But as you can see this is affected *a lot* (at least the random writes)! For both 4KB and 64KB random writes, performance increased 4 times after a trim!

Thanks for the instructions all!

BTW, I had to patch the wiper-script because Intel's drives are apparently not able to handle more than 512 ranges in one TRIM command ([http://www.ocztechnologyforum.com/forum/showpost.php?p=459615&postcount=112](http://www.ocztechnologyforum.com/forum/showpost.php?p=459615&postcount=112)). I'm including the patch to wiper-2.5.

---

### Post by runesvend on 2009-12-09
Hey apocalypse80. Do you have the second generation X25-M as well, or is yours the first generation?

I have the G2 but it seems my write speed (random or not) is capped at around 80 MB/s, also after trimming. Yours, on the other hand, goes all the way up to ~110 MB/s on 512 KB random writes, and is generally faster than mine it seems.
You also seem to have almost twice the read speed of my SSD when it comes to reading in 4 KB blocks non-randomly (not sure if that is sequentially or what).

I haven't done any of that "partition alignment on erase boundaries"-stuff, I just created 2 ext4 partitions (root and home) plus swap and hoped the Intel firmware would handle the rest.
Have you done anything out of the ordinary with your SSD? Do you have any idea why mine seems to be slower than yours?

---

### Post by tnttrx on 2009-12-09
btw, just in case anybody missed:

[http://www.dailytech.com/Intel+Issues+Fix+for+X25M+G2+SSD+Firmware/article17001.htm](http://www.dailytech.com/Intel+Issues+Fix+for+X25M+G2+SSD+Firmware/article17001.htm)

;)

---

### Post by apocalypse80 on 2009-12-16
> **runesvend said:**
> Hey apocalypse80. Do you have the second generation X25-M as well, or is yours the first generation?

It's a 160GB G2 with the latest firmware and I've done *everything*.

The trim-enabled firmwares also increase the write speed of 160GB G2s from 80MB/s to ~100MB/s, I also had a cap at ~85MB/s initially.
However the 80GB G2s **do not** get that speed bump, if you have one of those then yes your maximum will still be ~80MB/s.

The best indicator of whether everything's a-ok is 4k random writes.
If you have aligned and trimmed partitions then any intel G2 should get over 50MB/s, if you are much lower then something's missing.

In my case perfect alignment but untrimmed resulted in ~35MB/s @ 4k random writes.

---

### Post by Moondust on 2010-01-06
Has there been any 'official' news about when there's gonna be "automated" TRIM support? From what I've read also in the Lucid Lynx release it's not gonna be implemented, since it's still in early alpha anything could really happen.

Not a big problem of course, since you can just schedule or manual run wiper.sh._****_**[]("http://ubuntuforums.org/forumdisplay.php?f=377")**

---

### Post by antiram on 2010-01-17
yes, kernel-trim works with 2.6.33-rc4 and indilinx firmware 1916 and mount option -o discard.
deleting ~300MB small files results in: 
```

heiko@locutus:~$ uname -r; mount|grep sda6
2.6.33-020633rc4-generic
/dev/sda6 on /home type ext4 (rw,noatime,discard)
heiko@locutus:~$ sync
heiko@locutus:~$ time `rm -rf linux-2.6.29.4;sync`

real	0m1.378s
user	0m0.030s
sys	0m0.640s

```
if it really work you can test it:
get the used sectors for a file  
hdparm --fibmap filename
read a sector from the file eg. with
sudo hdparm --read-sector 66385920 /dev/sda
delete the file and sync
rm filename;sync
and read the sector a second time

---

### Post by josephellengar on 2010-02-26
I just tried running wiper.sh version 2.5 for the first time on my x25m gen2 and got the following terminal output: 
```

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (60944218 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 121888440 sectors from 1994 ranges
FAILED: Input/output error
Removing temporary file..
Syncing disks.. 
Aborted.

```

Anybody have any idea why that might be?  Thank you

---

### Post by josephellengar on 2010-02-27
> **runesvend said:**
> I just ran the wiper script on my 80GB X-25M Postville as well. Results:

```
BEFORE:

	Output is in Kbytes/sec
                                                            random  random
              KB  reclen   write rewrite    read    reread    read   write
          262144       4   32925   40142    44519    43749   17835    8443
          262144      64   81012   82615   199672   199854  140188   20138
          262144     512   34904   83236   249276   248545  227652   39838

AFTER:

	Output is in Kbytes/sec
                                                            random  random
              KB  reclen   write rewrite    read    reread    read   write
          262144       4   36490   40840    44292    44289   17956   37066
          262144      64   80661   81554   200097   198793  141341   80823
          262144     512   83239   59139   247916   248620  232914   80520
```

It seems that only the write performance is affected. But as you can see this is affected *a lot* (at least the random writes)! For both 4KB and 64KB random writes, performance increased 4 times after a trim!

Thanks for the instructions all!

BTW, I had to patch the wiper-script because Intel's drives are apparently not able to handle more than 512 ranges in one TRIM command ([http://www.ocztechnologyforum.com/forum/showpost.php?p=459615&postcount=112](http://www.ocztechnologyforum.com/forum/showpost.php?p=459615&postcount=112)). I'm including the patch to wiper-2.5.

How do I apply this patch to the script?  I'm not exactly sure what to do and I think that your problem with the 512 ranges might be why my attempt to use wiper didn't work.

---

### Post by jalyst on 2010-03-03
trim support in 2.6.33
[http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb](http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb)

---

### Post by tnttrx on 2010-03-03
and this could be very interesting for SSD users as they should avoid to much IOs (like swapping):

> 1.9. Compcache: memory compressed swapping

Recommended LWN article: Compcache: in-memory compressed swapping

Compcache is a project (still under development, only available in Staging) creates RAM-based block devices (/dev/ramzswapX) which are used as swap disks. Pages swapped to this virtual device are compressed to a smaller size. Part of your RAM is used as usually, and another part (the size is configurable) is used to save compressed pages, increases the amount of RAM you can use in practice.

This feature can be very useful in many cases: Netbooks, smartphones and other embedded devices, distro installers, dumb clients without disk, virtualization, or old machines with not enought RAM to run modern software.

Measurements have found this feature very effective. See this page to see some benchmarks. The project home page can be found at [http://compcache.googlecode.com/](http://compcache.googlecode.com/)

---

### Post by jalyst on 2010-03-03
very nice

---

### Post by josephellengar on 2010-03-03
> **jalyst said:**
> trim support in 2.6.33
[http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb](http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb)

Awesome!  When will it get rolled out in Ubuntu?

---

### Post by jalyst on 2010-03-03
Not sure sorry.
You can always roll it in yourself.

---

### Post by Radon on 2010-04-19
I'm pissed off that an LTS release isn't forward-looking enough to include TRIM.  

This will mean a reinstall of the OS every 2 months so that my SSD doesn't become slower than a normal HDD.

---

### Post by tnttrx on 2010-04-19
> **Radon said:**
> I'm pissed off that an LTS release isn't forward-looking enough to include TRIM.  

This will mean a reinstall of the OS every 2 months so that my SSD doesn't become slower than a normal HDD.

no-TRIM usage of SSD does slow down your drive, but it's helping you to kill it faster: wear leveling works much worse on non-TRIMed drive as controller doesn't know wich of blocks are not used by system.
(SSD controller uses free blocks to rotate them lovering wearing of one particular block)

---

### Post by nhasian on 2010-04-19
> **Radon said:**
> I'm pissed off that an LTS release isn't forward-looking enough to include TRIM.

Its easy to rectify.  Simply install the the linux kernel 2.6.33 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

then viola! you will have trim enabled when you boot with this kernel.

---

