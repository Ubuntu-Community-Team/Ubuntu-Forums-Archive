---
title: "Has anyone worn out a flash drive running Ubuntu from it?"
date: 2010-10-17
forum: Hardware
---

### Post by C.S.Cameron on 2010-10-17
Many people think that running Ubuntu from a flash drive will quickly wear it out.
I have been running a full install on a Kingston flash drive for over three years without problem.

I am wondering if anyone here has actually worn out a flash drive doing so.

If so:
- Were you running a Full install or a Persistent one?
- How long did it take to wear it out?
- What was the make of the drive?
- Was your data still accessible after failure?
- Could failure have been due to another reason, such as unsafe removal or a bad format?

---

### Post by C.S.Cameron on 2010-10-18
Bump

---

### Post by Pickel on 2010-10-18
Have been running from flash drive for almost a year now and it seems to work fine. 
I have done some changes to lessen the wear thou, /tmp is tmpfs and logging is minimized.

---

### Post by C.S.Cameron on 2010-10-19
> **Pickel said:**
> Have been running from flash drive for almost a year now and it seems to work fine. 
I have done some changes to lessen the wear thou, /tmp is tmpfs and logging is minimized.

Has anyone else been running Ubuntu from a pendrive for over a year without wearing it out?

---

### Post by DZ* on 2010-10-19
> **C.S.Cameron said:**
> Has anyone else been running Ubuntu from a pendrive for over a year without wearing it out?

I did a full install on a 16 Gb Kingston DataTraveler in May 2009. I didn't bother with disabling journaling. It hasn't been used heavily but I would at least update it about once a week and write/compile some LaTeX files between home and work. Then I put Karmic on it and next upgraded to Lucid. It has the default ext4 and still works fine. At first I used full-stick encryption (too slow), then switched to ecryptfs-ed account. I did some write speed tests and it appears that the bottleneck is with the USB access, that is, ecryptfs doesn't slow down write speed any further on a USB install.

---

### Post by snowpine on 2010-10-19
Running various distros (currently 9.04) from a cheapo 8gb flash drive for almost 2 years. No problems. I'm currently using ext4 with the "noatime" flag and no swap.

---

### Post by C.S.Cameron on 2010-10-21
Bump

---

### Post by lukeiamyourfather on 2010-10-21
> **C.S.Cameron said:**
> Bump

Why do you keep bumping the thread, people have replied. Relating to the topic, if a system will be running for several years then I'd suggest installing it to a hard disk. While it might work for some, USB flash drives have the potential to fail much more frequently than hard disks when used as a boot disk. Most will accept 1,000 writes per cell or less. Log files and swap could easily exceed that if there wasn't much space left on the drive (i.e. the unused cells would be written to more frequently). Though if there isn't an alternative then a flash drive has proven it can work in some situations.

---

### Post by C.S.Cameron on 2010-10-21
> **lukeiamyourfather said:**
> Why do you keep bumping the thread, people have replied. Relating to the topic, if a system will be running for several years then I'd suggest installing it to a hard disk. While it might work for some, USB flash drives have the potential to fail much more frequently than hard disks when used as a boot disk. Most will accept 1,000 writes per cell or less. Log files and swap could easily exceed that if there wasn't much space left on the drive (i.e. the unused cells would be written to more frequently). Though if there isn't an alternative then a flash drive has proven it can work in some situations.

Thanks Luke:
The reason I keep bumping this thread is that I have heard people claim that running an O/S from flash drive wears it out, however I can't find much evidence of this in the real world.
Manufactures claim 10000 - 100000 writes plus wear leveling, which spreads out use over the drive. Doing the math, I figure a flash drive should last years when used to run an O/S.
Pendrives are great for giving people confidence in Linux, I hate to see them scared off by misinformation.

---

### Post by lukeiamyourfather on 2010-10-21
> **C.S.Cameron said:**
> Thanks Luke:
The reason I keep bumping this thread is that I have heard people claim that running an O/S from flash drive wears it out, however I can't find much evidence of this in the real world.
Manufactures claim 10000 - 100000 writes plus wear leveling, which spreads out use over the drive. Doing the math, I figure a flash drive should last years when used to run an O/S.
Pendrives are great for giving people confidence in Linux, I hate to see them scared off by misinformation.

Typical flash cells last for 1,000 write cycles per cell (some are more and some are less), not 100,000 despite what manufacturers advertise. Note Western Digital and Seagate say their drives have an average failure time of millions of hours (which is also not true) so take those numbers with a grain of salt. As far as I know USB flash drives don't have wear leveling like 2.5" SSD have.

Longevity and reliability aside, USB simply doesn't have the throughput compared to SATA, SAS, etc. So even if it technically is possible to use a USB flash drive for a boot disk, most people wouldn't want to anyway. There's also other factors to consider like a flimsy piece of plastic sticking out of the computer that is easily broken. Capacity is another deal breaker since hard drives are an order of magnitude or two bigger. I'd still suggest using a hard disk (or at least SSD) for long term installations.

---

### Post by C.S.Cameron on 2010-10-21
> Typical flash cells last for 1,000 write cycles per cell (some are more and some are less), not 100,000 despite what manufacturers advertise. Note Western Digital and Seagate say their drives have an average failure time of millions of hours (which is also not true) so take those numbers with a grain of salt. As far as I know USB flash drives don't have wear leveling like 2.5" SSD have.

Thanks Luke:
What do you base this on, Personal experience?

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by lukeiamyourfather on 2010-10-21
> **C.S.Cameron said:**
> Thanks Luke:
What do you base this on, Personal experience?

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

I'm pleasantly surprised to see the USB flash drive lasted so long in that test as I use flash drives often for other purposes. As for where I got the number, 1,000 write cycles per cell has been thrown around a lot. Even in specifications for many flash memory products and from flash memory manufacturers. 

> For one thing, it matters whether the SSD drive uses SLC or MLC memory. SLC generally endures up to 100,000 write cycles or writes per cell, while MLC can endure anywhere from 1,000 to 10,000 writes before it begins to fail, according to Fujitsu's Hagberg. For its part, Western Digital's laptop hard-disk drive boasts up to 600,000 write cycles.

[http://www.computerworld.com/s/article/9112065/Solid_state_disk_lackluster_for_laptops_PCs?taxonomyId=19&pageNumber=4](http://www.computerworld.com/s/article/9112065/Solid_state_disk_lackluster_for_laptops_PCs?taxonomyId=19&pageNumber=4)

Of course there are exceptions to this and things might be better by now since that is from 2008. Though I still wouldn't use a USB flash drive as a replacement for a hard drive for all the other reasons previously mentioned (insufficient throughput, very little storage space, etc.). It would be nice to see products from other manufacturers subjected to similar testing to see how they fare. Thanks for the link to that flash drive testing.

---

### Post by friTTe81 on 2010-10-21
Will keep on checking this thread out, this is actually really interesting.
Seen alot of people using ssd in their netbooks and says it works really good, but i have always had that "tearing" in my mind.

But seems that isnt such a biggie

---

