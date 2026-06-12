---
title: "DMA IDE errors. SMART finds bad crcs...all *new* drives"
date: 2008-04-22
forum: Hardware
---

### Post by ABX323 on 2008-04-22
A hint or some help would be wonderful.

I have a pc with 4 hard drives, I installed XPpro on it and it worked wonderful.
Got ubuntu 7.10 on it now as a samba server. The main HDD is slightly older, but the other 3 are brand new 500 gig WD ata100.
2 are still ntfs from XP, the other I reformatted and is ext3 to test.

When I mount them and try to read files the kern.log goes ape spewing out:
hdX: dma_intr:status=0x51 {DriveReady SeekComplete Error }
hdX: dma_intr:status=0x84 {DriveStatusError BadCRC }
ide: failed opcode was:unknown
replace the X after hd with a,b,c,d.
I don't want to damage these new expensive drives. A smart test says they pass, but the crcs are incredible. over 6000 on the 500gig ata that I just formated it to ext3 and it only has 2 files in it. WTF?

I did not check to see anything was wrong till I noticed that read/write times on all but the booting hdd are as slow as 10baset ethernet. I'm not kidding. 7 minutes to move a 80mg file.
read/write on the boot hdd are maybe 1/3rd USB ver2 speed.

---

### Post by ABX323 on 2008-04-22
I also want to add (and subscribe to this thread) that when I took the main HDD out of the case to boot windows to check the new drives, it was piping hot, even though I made that last post with a different pc and the Ubuntu pc was idle for over an hour.

---

### Post by Moop on 2008-04-22
I don't know anything about the errors but I don't think the hdd should be piping hot! They get warm but shouldn't be to hot to hold. 

Have you tried the hdd's one at a time? Maybe you have a power problem with adding 3 more hdd's and it's more than the PSU can handle.

---

### Post by ABX323 on 2008-04-22
> **Moop said:**
> I don't know anything about the errors but I don't think the hdd should be piping hot! They get warm but shouldn't be to hot to hold. 

Have you tried the hdd's one at a time? Maybe you have a power problem with adding 3 more hdd's and it's more than the PSU can handle.


I have not tried just the root filesystem alone with ubuntu, but I did with xp and 2003server and there was no issue.
I had such a flawless install in my crummy gateway laptop, I just changed hard drive trays with a new hdd with gutsy on it.

The aforementioned hdd was in a 3 fan kingwin cooler tray and the smart output showed drives with Spin_Up_Time in the 3-6 thousand range.

The facts don't make sense to me. The older drive has a write time 10 time faster then drives I bought 2 weeks ago.

Disabling DMA did not make the situation better or worse.

---

