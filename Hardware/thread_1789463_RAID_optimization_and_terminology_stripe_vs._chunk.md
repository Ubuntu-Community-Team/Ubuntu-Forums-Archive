---
title: "RAID optimization and terminology: stripe vs. chunk vs. cluster vs. block"
date: 2011-06-23
forum: Hardware
---

### Post by zephyr707 on 2011-06-23
Hello all,

been banging my head on this problem for the last couple of hours and I continue to turn up conflicting information wherever I look.  Any RAID experts out there that can help clear things up for me?  I'm trying to figure out the difference between various RAID terminology: stripe size, chunk size, cluster size, block size.

From my current understanding of RAID, a stripe is made up of chunks.  The chunk size determines various performance characteristics depending on what type of data you are working with and the average I/O operations.  The chunk size and number of drives (stripe width) determines the stripe size (basically: chunk size * stripe width = stripe size).
A cluster is a collection of blocks, where cluster size is determined at the file system level and block size determined at the physical hard disk level.  To make things confusing, cluster size and block size are sometimes meant to mean the same thing...
So I think chunk size is for the RAID controller and cluster/block size is for the operating system (assuming hardware RAID).  But it seems that the optimal size for these 2 parameters is somewhat counter intuitive.  For video, it seems like you want a smaller chunk size, but a larger cluster/block size, is that correct?  

[This  article]("http://www.tomshardware.com/reviews/RAID-SCALING-CHARTS,1735-4.html") from tomshardware.com seems to conflict with [this other article]("http://www.zdnet.com/blog/storage/chunks-the-hidden-key-to-raid-performance/130") from zdnet.  I think the zdnet article is correct, smaller chunk size = better performance for large data such as video, but I am thoroughly confused now after all my research.  This [pdf from xyratex ]("http://www.xyratex.com/pdfs/whitepapers/Xyratex_White_Paper_RAID_Chunk_Size_1-0.pdf")helped illuminate some things, but I think the terminology is quite confusing and just googling around I don't appear to be the only one confused...

Any help would be greatly appreciated,

thanks!
zephyr

---

### Post by tgalati4 on 2011-06-23
Don't use RAID.  Get more RAM and you won't need to screw around with RAID parameters and RAID failure.  Modern SATA disks have enough throughput and enough buffering, that any increase in disk throughput through RAID is countered by increase risk in failure.

Also large disks suffer from long rebuild times when the RAID has degraded--sometimes several hours.  A failure during this rebuild time can mean complete RAID failure at that point.

Unless your network is 10 gigabit, network latency will kill any RAID benefits.

As for terminology, hardware RAID controllers are optimized for a certain range of chunk size and stripe layout.  In a Dell PowerEdge 1750 server with a PERC4/Di RAID controller, you only have room for 3 disks so you are striping across 3 disks (typical RAID5 configuration) and in linux you are using the megaraid driver.  There are some configuration tools to tweak the RAID performance and I don't recall what the specs are but a little googling:

[http://www.amazon.com/Dell-Poweredge-1750-Server-Y0229/dp/B00456Y41G](http://www.amazon.com/Dell-Poweredge-1750-Server-Y0229/dp/B00456Y41G)

Host data transfer rate : 532 MB/s
Drive data transfer rate : 320 MB/s
Maximum size of I/O requests :6.4 MB in 64 KB stripes
Maximum queue tags per drive : As many as the drive can accept
Stripe sizes : 2 KB, 4 KB, 8 KB, 16 KB, 32 KB, 64 KB, or 128 KB

So for hardware RAID, it depends on your hardware, obviously, but for FakeRAID and software RAID, you would have to perform testing to find optimum settings.

In the above PERC example, the disks are u320 SCSI, so you can't expect more than 320 MB/sec and typical 15,000 rpm drives can put out ~70 to ~100 MB/sec due to physical limitations.  The card can only transfer 532 MB/sec to the motherboard.  The RAM tested out to ~3,000 MB/sec as I recall.  So with 3 disks in a stripped configuration, you are looking at 70*3 or ~270 MB/sec sustained write speed.  You can tweak the stripe size but it's a broad curve and it really depends on your workload.

In the PERC example, I think chunk size is 6.4 MB maximum using 64 kB stripe size.  I don't know if there is an optimum.

There's a decent collection of performance tools that you can install:

sudo apt-get install phoronix-test-suite

I ran a bunch of performance tests, but I don't have the results handy.  I did find a single drive test:

/dev/sdb1:
 Timing cached reads:   1364 MB in  2.00 seconds = 681.81 MB/sec
 Timing buffered disk reads:  226 MB in  3.01 seconds =  75.20 MB/sec

So, to answer your question, there is no standard nomenclature for either RAID configuration or performance parameters.  There are accepted and commonly used terms.  Selection of optimum parameters can only come about with extensive testing using the disks, RAID controller and representative workloads.

After a little more searching I found this thread:

[http://www.thegeekstuff.com/2008/07/step-by-step-guide-to-configure-hardware-raid-on-dell-servers-with-screenshots/](http://www.thegeekstuff.com/2008/07/step-by-step-guide-to-configure-hardware-raid-on-dell-servers-with-screenshots/)

The definitive guide says:

Keep the default settings!

---

### Post by zephyr707 on 2011-06-24
Hi tgalati4,

thanks for your reply.  I think your advice is solid, stick with the defaults!  I found out that the hardware raid in my RAID enclosure is 512b chunks and it is not changeable, so not much choice there =)  I was more curious about the terminology than anything, which it sounds like is just plain  confusing and somewhat interchangeable depending on which page you are reading or who you talk to.

as for increasing RAM vs. using RAID, I am committed to RAID10 or at least RAID1 for the backup.  I feel more comfortable knowing that if a drive fails I can throw in a spare and it will mirror again w/o losing any data.  I lost a drive once to hardware failure (horrible sound of head scratching the platters) and the  recover quote was several thousand dollars.  I backup everything now in case of hardware failure.

thanks
zephyr

---

### Post by tgalati4 on 2011-06-24
Just remember that RAID is for speed and uptime, not backup.  It really isn't suited for protecting data.  You need other strategies to cope with data loss.

---

### Post by RayChangTW on 2011-06-25
[tgalati4]("http://ubuntuforums.org/member.php?u=241895"), your post is very informative.  I have been wondering these things for a long time.  Thank you.  I'm in a RAID mess at the moment and need all the help I can get.  (I have created a new thread for my Nvidia problem).  

Thanks again.

---

### Post by zephyr707 on 2011-06-27
to me RAID1 seems like a cheap way to back things up in case of hard drive failure.  I suppose I could rsync it to another drive or rsync to a remote location, but that seems more time consuming or expensive.  I'm not really concerned with any kind of incremental backup like apple's time machine, just drive failure.  I've found that RAID10 gives me a speed boost and peace of mind, and i don't have to have any kind of backup software or daemon running.

what do you recommend as a backup solution?

thanks
zephyr

> **tgalati4 said:**
> Just remember that RAID is for speed and uptime, not backup.  It really isn't suited for protecting data.  You need other strategies to cope with data loss.

---

