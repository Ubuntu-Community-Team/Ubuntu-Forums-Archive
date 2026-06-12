---
title: "Nightmare intermittent hardware problem"
date: 2009-01-15
forum: Hardware
---

### Post by Midahed on 2009-01-15
I'm trying to test Intrepid with a RAID and encryption on a spare PC before installing it on my main Ubuntu box.

The system keeps crashing.  Initially I thought it was a problem with Intrepid + RAID + encryption, but it seems that isn't likely.

After a great deal of swapping stuff around and trying various installations of 8.10 and 8.04 I'm pretty sure it's a hardware fault, but it's very intermittent.

It's not Ubuntu because it's crashed with 8.10 and 8.04.  It's even crashed when running DBAN (the bootable linux-based disk wiping program).  It also crashes during Ubuntu installs - a favourite time being when manually setting-up the partitioning, especially during the configuring of the raid partitions into md devices.

I've swapped IDE channels, the IDE controller itself, the PATA cable and the disk drives themselves, but the box continues to crash eventually, even though it sometimes takes 24 hours to do so.

I've swapped the memory banks around and run memtest86 for a day or two without any problems being reported.

I was beginning to think it was one of the drives, but changing them both along with the IDE cable has left me with the same problem.

I suppose the next thing to try is the PSU, but I've been avoiding that because I don't have a spare test unit unless I rip it out of my main machine.  The 'health' report of the voltages on one of the BIOS screens looks OK - all the voltages are stable within the range of 0.1v and are within spec.  The BIOS config is set for 'stable' - the PC's not being over-clocked.  It's been used like that for several years as a Windows machine and has been fine throughout that time.

Have I missed anything?

Also, does anyone know of a really good testing program that allows every aspect of a PC to be hammered at the same time.  I'd like to find something that will cause it to crash more frequently, rather than spending many hours waiting to see if something I've changed makes any difference.  There are plenty of simple tests, but they all seem to just test one aspect of the machine.  Of the ones I've tried, even the disk tests are only capable of checking a single drive at a time.

Thanks,

Mike

---

