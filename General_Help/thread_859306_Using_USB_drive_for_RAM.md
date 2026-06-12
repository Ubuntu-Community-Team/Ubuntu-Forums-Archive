---
title: "Using USB drive for RAM"
date: 2008-07-14
forum: General Help
---

### Post by Shaided on 2008-07-14
Can you do this on Ubuntu and how....?

---

### Post by Rainstride on 2008-07-14
i know using gparted you can format a flashdrive to swap but im not sure how to have your system use it as the main swap, or what would happen if it was unplugged by accident.

---

### Post by Shaided on 2008-07-14
any help here....

---

### Post by fyo on 2008-07-14
I'm not sure I understand what it is you want to accomplish.

Using an USB drive, or any other flash-based memory solution, as RAM is generally a bad idea since it has an extremely limited lifetime in terms of number of writes.

---

### Post by estyles on 2008-07-14
I believe you're referring to the new feature in Vista - ReadyBoost, which uses a USB drive as a cache.  I'm 90% certain that Ubuntu doesn't support this, and to be honest, I'm not sure why you'd want to do that.

The two options for a USB ReadyBoost are an internal USB header and an external USB drive.  For an external drive, I can't imagine that it's faster than using a swap file on the HD - and HD's are way cheaper by GB than a USB flash drive.  For an internal header, I can see how it would be a faster cashe than using hard disk space, but with RAM prices being so low, I'd rather get an extra 1GB of RAM for a much more noticeable effect - as long as I'm mucking around inside anyway, and an internal flash drive that connects to a USB header is a fairly specialized piece of equipment.

I don't know a whole lot about this feature, but it seems somewhat poorly conceived.  The ideal use for it would be for non-technical users to easily revitalize an older system by simply plugging in a USB drive, but a system that old doesn't seem like it would be able to run Vista very well anyway, and an extra gig or two of cache space shouldn't make all that much difference.

Personally, I'd rather use the flash drive for storage and make a bigger swap partition on my HD.

---

### Post by Squid Tamer on 2008-07-14
I don't think it would be a good idea... a flash drive will only survive up to 100,000 writes, and that can go by very quickly with ram.  

Assuming you know what your doing, you could try to format it to linux-swap in gparted, but I don't know if it will work or not.

---

### Post by diwas on 2008-07-14
I dont think its possible coz RAM has considerably large computin speed. And i guess USB flash drive wont be enuf to replace it. Or in other words 10Mbps isnt enuf for RAM. 
I might be wrong though.

---

### Post by YaroMan86 on 2008-07-14
It's technically possible, since Vista has ReadyBoost.

Adviseable or practically possible is another story.

---

### Post by sayakb on 2008-07-14
You can format a USB Flash Drive as swap but it would be in no way a replacement for a RAM. Standard USB drives have a speed of <10MB/s and a good RAM has 3000+MB/s speed.. there is absolutely no comparison.

---

### Post by LowSky on 2008-07-14
Readyboost is based on the idea of Swap space, but instead of using a space on your hard drive you use a flash drive which frees up the bus lines and hard drive cache. The dowpoint is a USB used Readyboost or Swap wont last very long.

---

### Post by estyles on 2008-07-14
I did a little bit more research on ReadyBoost, and a few of the concerns are answered:

1) Supposedly, according to MS testing, a flash drive used as a ReadyBoost should last 10+ years.  I don't know if that's necessarily true, but it shows they are at least aware of the issue of lifetime, and have taken some steps to avoid unneccessary writes.

2) The USB drive is supposedly faster for random reads of small bits of data.  Apparently faster than a HD for reads of under 512KB.

3) The same data is backed up on the paging file on disk, so it won't be lost if you unplug the drive.  I'm not sure how this would affect performance, but it seems to negate about half the point of actually using it.

4) The data is encrypted, so it's not a security risk.  Again, I feel like this would further affect performance...  so it's faster than a bigger swap file on the HD... how?

All in all, I'm betting the performance gain is almost negligible, and you'd be better off just buying an extra gig of RAM...  RAM is cheap these days!

These points also say to me that just formatting a USB drive as a swap drive in Linux would be a bad idea, and wouldn't be quite the same thing as readyboost at all.  But I still don't see how it could help all that much.

---

### Post by lavinog on 2008-07-14
> **estyles said:**
> 
I don't know a whole lot about this feature, but it seems somewhat poorly conceived.  The ideal use for it would be for non-technical users to easily revitalize an older system by simply plugging in a USB drive, but a system that old doesn't seem like it would be able to run Vista very well anyway, and an extra gig or two of cache space shouldn't make all that much difference.

Personally, I'd rather use the flash drive for storage and make a bigger swap partition on my HD.

I think part of the reason for it is in the near future vista will require 3+ gigs of memory leaving little to no room for cache. Since many vista systems are 32bit they won't be able to take advantage of more than 4 gigs of ram...using the flash drive as memory is a cheap hack to get around this issue.

the lifetime issue is not a major deal. Each bit can have a life of 100,000+ writes. Since the firmware handles wear leveling you have to write 8*10^14 bits before failure of a 1 gig flash drive. There are other features of flash drives that minimize wear on them too.

Since linux apps share more libraries than windows apps, and are usually cached already. I would doubt that anyone would see any performance gains if readyboost was implemented in linux.

Like mentioned before adding ram is much more effective...it is much faster than flash media...and it is designed to be a cache storage. Flash is designed for long term storage not speed.

---

### Post by Settwi on 2010-01-17
Why would you want to do this, exactly?  lavinog, you made a good point, but if someone REALLY wanted a bunch of memory, (and they have a big harddisk) Just allocate like 2-3GB of it as virtual memory.  Works the same, why not just do that?   sure it's not as fast as a 800MHz stick but it's ram!
:grin:

---

### Post by carlosgs91 on 2010-01-17
.

---

### Post by LoneWolfJack on 2010-01-17
Here's a simple example on why a USB drive will NEVER be able to replace RAM:

USB 2.0: 60 MB/s
PC2-5400 DDR2-SDRAM: 10000.7 MB/s
PC3-16000 DDR3-SDRAM: 48000.0 MB/s

What ReadyBoost draws upon is the fact that flash drives of any kind have WAY lower seek times than normal drives, which makes them interesting as swap drives. However, this advantage only holds up as long as only small files are requested from the drive.

You should rather go an see if you can do something about your RAM. If you have enough RAM, you don't need swap at all...

---

### Post by kerry_s on 2010-01-17
threads from 2008, let it be. ;)

---

### Post by sports.car.guy on 2010-01-17
It is very possible to use a USB drive as swap but why would you want to. All you need to do is set the drive to mount always to the same place by ID and that should be it. You can partition it fully as swap or a portion of it, it's up to you.

It is like using any other dirve why think of it as so complicated because it is USB.

---

### Post by pablo180 on 2010-02-26
> **Settwi said:**
> Why would you want to do this, exactly?  lavinog, you made a good point, but if someone REALLY wanted a bunch of memory, (and they have a big harddisk) Just allocate like 2-3GB of it as virtual memory.  Works the same, why not just do that?   sure it's not as fast as a 800MHz stick but it's ram!
:grin:

Because a USB stick is faster. Also, if you're reading programs and information from the same drive as you're writing to, that is going to slow things down even more, in some cases (backing up in the background) way more. 

A USB swap drive does give a speed boost, my laptop hardly ever grey screens now when backing up or doing other intensive tasks, I just wish there was a way of making the change permanent.

---

### Post by lavinog on 2010-02-26
> **pablo180 said:**
> Because a USB stick is faster. Also, if you're reading programs and information from the same drive as you're writing to, that is going to slow things down even more, in some cases (backing up in the background) way more. 

A USB swap drive does give a speed boost, my laptop hardly ever grey screens now when backing up or doing other intensive tasks, I just wish there was a way of making the change permanent.

USB drives have the extra IO overhead restricting the speed even more.  If using a usb drive as swap, there will be a performance hit since usb flash drives cannot do DMA transfers.

A better solution would be to get a sata compact flash reader for $15 and a decent high speed CF card.  This would be a more reliable solution since the reader can be used internally.

I don't know what type of error checking the kernel does on pages in swap.  A single bit error could take down the whole system, but this is true when the system uses a hard drive as swap also...so does the kernel have any redundancy when swapping?

edit: For laptops, you might be able to use the pcmcia or pci express slot to hold a 8g ssd (newegg has had a couple for under $40)

---

### Post by pablo180 on 2010-02-27
> **lavinog said:**
> USB drives have the extra IO overhead restricting the speed even more.  If using a usb drive as swap, there will be a performance hit since usb flash drives cannot do DMA transfers.

A better solution would be to get a sata compact flash reader for $15 and a decent high speed CF card.  This would be a more reliable solution since the reader can be used internally.

True, there are better options, but I think that the original poster, and certainly myself were looking for a cheap and easy alternative to purchasing RAM, something like ReadyBoost for Windows. Most of us have unused 2GB+ USB drives or flash cards lying around. 

In my case my 1GB RAM is ample, I rarely use more than 60%-70% of it, however for some reason since the upgrade to Karmic when I start using 50%+ RAM it starts using the Swap disk, apart from a little slowdown this isn't too much of a problem until it is carrying out a daily back up, installing or updating, which then renders the laptop almost unusable. 

The best choice would be more RAM, however my laptop has 2 X 512MB, which means I'd need to get 2 x 1GB replacements (at about $60+), not really worth it as I rarely use more than 60% of my RAM. 

Formatting an SD card as swap and sticking it into the built in card reader has made things much smoother, I don't notice it doing the backups in the background anymore (I used to just go and make a cup of tea till it was finished). Nor do I get so many grey screens during installations or backups. 

So I would definitely recommend it over using the hard drive as swap alone. But obviously it's not a replacement for RAM. 

> **lavinog said:**
> I don't know what type of error checking the kernel does on pages in swap.  A single bit error could take down the whole system, but this is true when the system uses a hard drive as swap also...so does the kernel have any redundancy when swapping?

There is definitely something different. It usually resumes from standby without problems but if I have left it in standby for a few hours, I get a screen of read/write errors on the card and then logged out. I'm not sure whether this is to do with me knocking the card out accidentally, or whether the card reader isn't coming back on (as it only seems to happen after a long standby), but it is a little annoying.

---

### Post by lavinog on 2010-02-27
> **pablo180 said:**
> 
In my case my 1GB RAM is ample, I rarely use more than 60%-70% of it, however for some reason since the upgrade to Karmic when I start using 50%+ RAM it starts using the Swap disk, apart from a little slowdown this isn't too much of a problem until it is carrying out a daily back up, installing or updating, which then renders the laptop almost unusable. 


Try uninstalling ureadahead:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)
[http://ubuntuforums.org/showthread.php?t=1363165](http://ubuntuforums.org/showthread.php?t=1363165)

---

### Post by ValentineX on 2010-08-28
In Windows XP in My computer properties, Advance, Cache option I have setup my USB to share memory with system as cache. It has significantly increased my system speed. This is what the topic author is asking for ubuntu and the same I am looking for USB disk memory use as RAM or Cache in Ubuntu.

---

### Post by pablo180 on 2010-08-28
> **ValentineX said:**
> In Windows XP in My computer properties, Advance, Cache option I have setup my USB to share memory with system as cache. It has significantly increased my system speed. This is what the topic author is asking for ubuntu and the same I am looking for USB disk memory use as RAM or Cache in Ubuntu.

While it is possible, it isn't really worth the hassle. You can (as I did) format a USB drive or SD card as a swap disk (or cache), and then use that as a faster cache than the hard drive, but I had all sorts of problems. 

Firstly, it isn't possible to make the change permanent, because on each boot, the swap disk on the HD gets priority, presumably because during boot the USB drivers aren't enabled first, negating the point of having a USB swap disk. I had to change the swap priorities every time I logged in. 

The other problem I had was that on resuming from a long suspend (a couple of hours) the SD card didn't seem to wake up, causing a crash and logging me out. It didn't always do it, but just enough to make it really annoying and inconvenient. 

I also had a problem hibernating, seemingly for the same reason and hibernation became very hit and miss. 

Using a USB drive as a swap disk did give me a speed boost, but the other problems just made it too unreliable and outweighed the benefits. I tried following lavinog's advice, that unfortunately didn't help so in the end I just forked out for some more RAM and got two 2GBs RAM sticks. 

That gave me a massive speed boost, but it is worth noting that I still, rarely use more than 750MB of RAM, and it still writes to the swap disk, so I think something changed in Karmic and Lucid in the way that the OS uses the RAM and swap disk (possible presuming everyone has gigs of RAM) and it has slowed down Ubuntu quite a bit. I never had this problem before Karmic, and I don't have it now I have 4GB of RAM, but it seems strange that 1GB of RAM was fine, and then suddenly it wasn't.

So if you're looking for a speed boost, sadly the only real option is more RAM.

---

### Post by lavinog on 2010-08-28
> **pablo180 said:**
> 
That gave me a massive speed boost, but it is worth noting that I still, rarely use more than 750MB of RAM, and it still writes to the swap disk, so I think something changed in Karmic and Lucid in the way that the OS uses the RAM and swap disk (possible presuming everyone has gigs of RAM) and it has slowed down Ubuntu quite a bit. I never had this problem before Karmic, and I don't have it now I have 4GB of RAM, but it seems strange that 1GB of RAM was fine, and then suddenly it wasn't.


There was an issue with ureadahead for both karmic and lucid where it was allocating 128M of ram and never freeing it when it was done.
There is a fix in the proposed updates, but it still grabs 128M even though I don't think it would ever need 32M.

---

