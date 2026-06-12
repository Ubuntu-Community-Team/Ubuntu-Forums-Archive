---
title: "Difference between a 7200 rpm HDD and 5400 rpm HDD"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by BrokeBody on 2007-06-06
I'm just curious. How big difference is between a 7200 rpm HDD and 5400 rpm HDD on the same hardware?

---

### Post by tturrisi on 2007-06-06
7200 rpms - 5400 rpms = 1800 rpms = 25% of 7200 rpms

---

### Post by Hisstareia on 2007-06-07
> **tturrisi said:**
> 7200 rpms - 5400 rpms = 1800 rpms = 25% of 7200 rpms

More or less, its a speed thing, or how many *revolutions per minute* the drive can do. If you do a lot of reading and writing to the drive (i.e. saving and reading large files) you'll see a big difference in speed between the two.

---

### Post by BrokeBody on 2007-06-07
> **tturrisi said:**
> 7200 rpms - 5400 rpms = 1800 rpms = 25% of 7200 rpms

:D

I meant, is it very noticeable?

---

### Post by firdooze on 2007-06-08
i just upgraded my laptop hdd from a 5400rpm to 7200rpm

i can say that there isn't much difference on ubuntu or windooze. However there is noticeable difference if I use programs like Gimp and matlab.

---

### Post by bergersau on 2007-06-08
As a rule the faster the drive spins the more heat it'll generate.
10000 RPM  Raptors run hot as hell...

If you have enough RAM there will be less of a noticeable difference in speed.
Swapping/paging data from RAM to Hard drive and back is what will kill performance big time and the slower the drive the bigger the performance hit.

Also the slower the RPM the longer the seek times will be.

---

### Post by CrispyFried on 2007-06-08
platter density and cache play a  role too, in some situations (writing many small files such as databases) a 5400 drive with high density and a large cache can out perform a 7200 drive with lower density and smaller cache, but most new 7200 drives have both high density and big caches so it probably doesnt matter much anymore. 

if youre on older hardware (running UDMA 4 or less, say)  it can barely keep up with 5400 drives to begin with so there wont be much difference.. new hardware (UDMA6 or SATA) can take advantage of faster drives.

I tend to put the OS on the 7200 and data on the 5400 when Im on a machine with both as you can find big 5400 drives cheap.

---

### Post by mifi on 2007-06-08
> **CrispyFried said:**
> platter density and cache play a  role too,
They do.

And most important is the way it is used. If the drive has to do a lot of seeks that are not repeated, the cache will not contain the data so it has to be read. Reading can only take place when the data is below the head and that will take positioning the heads and then wait half a revolution on average. It is this half revolution that will take less time on disks that spin faster.

The speed with which the data will be read depends on the data density and the rotational speed.

If you will notice a difference therefore totally depends on the amount and kind of disk accesses that your applications use. Are they disk intensive, memory intensive or processing intensive?

For a normal household PC in normal use (i.e. browsing, email, some wordprocessing), my guess would be that the difference in hardly noticable. For database servers, depending on the pattern of disk activity, there can be large differences.

m

---

### Post by CrispyFried on 2007-06-08
> **mifi said:**
> 
And most important is the way it is used.


definately. if youre into video editing or big databases they can make a big difference*** if*** your hardware can keep up. but for browsing and WP probably no difference.

about the only thing I noticed when going from a 5400 to 7200 was decreased boot time and faster game loads. once the game level loaded there was no increase in FPS or anything, thats proc and memory/video card bound, not HD. system responsiveness stayed about the same, some programs (open office for example)  loaded a bit quicker but not by much.

as mifi asked, what do you do with your box? and what hardware do you have? depending on your answer, stuffing more ram into your box might be a better investment. more ram = less disk swapping. for example the way I use my PC (many apps open at once but not much of them do heavy disk access once loaded) an extra gig of ram would help me more than a 10,000 rpm drive. but I dont do much database or video editing.

---

