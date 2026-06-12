---
title: "Memory not being fully detected"
date: 2011-12-23
forum: Hardware
---

### Post by Stephan1864 on 2011-12-23
I recently installed Ubuntu 11.10 64-bit. I also just got two sticks of 2G DDR 400Mhz ECC Reg. Ram for my computer (It requires ECC Reg for anything a Gig and Up) for a total of 6 Gigs. The motherboard is an H8DCE, if that helps. 

Anyway, I installed the ram yesterday, and at first it would detect it all in the bios, but not in Ubuntu (Which only detected 4.8). Then I switched the new ram onto one processor on alternating DIMM slots, and it detected correctly (at 5.8 Gigs). But when I booted up today, it wasn't detecting it correctly in the bios or in Ubuntu, as both were getting 4.8 Gigs. I swapped the positions of the new Ram (trading places) on the CPU they were attached to. Now the Bios is detecting 6 gigs (roughly), but Ubuntu is not, and is still only reading 4.8. Also it seems that the computer has slowed down some since I installed the new ram (they're all PC3200 though). I'm out of ideas. Need help.

---

### Post by dabl on 2011-12-23
The motherboard specs say "2.5V only" for the DIMMs.  Did you verify that for your DIMMs?

---

### Post by Stephan1864 on 2011-12-23
> **dabl said:**
> The motherboard specs say "2.5V only" for the DIMMs.  Did you verify that for your DIMMs?

Yes, the Ram is 2.5 V. I had 2 Gigs before hand, and I had gotten it to read 6 gigs (5.8 actually) at one point. But when I booted it up this morning it was back to 4.8, and the bios was reading 4.8. It's not being read properly, and I'm loosing basically 1.2 gigs of RAM into the ether.

It's now down to 4.7. I just changed my video card, so not sure if that matters.

---

### Post by dabl on 2011-12-23
The BIOS reading will reflect what the CPU can see on the memory bus.  Linux will not find more than you see in BIOS.

---

### Post by Stephan1864 on 2011-12-23
Just ran Memtest. No errors. The Bios will recognize 6 Gigs when I swap the memory around on the board. But after a reboot doesn't anymore. Not sure what's going on there. I'm going to try just running the new Ram, and seeing if I get the 4 gigs, then testing each chip to find where the problem pops up. Might be something to do with the Bios, or the Ram itself. Will know soon.

---

### Post by Stephan1864 on 2011-12-24
Ok, Just running the new Ram, shows 2.8 Gigs of ram on two 2 Gig chips. However, when I runn dmidecode type 17, it tells me that my DIMM0 and DIMM4 are running chips with size 2048 MB, the rest reading as 64 MB (I have 8 DIMMS in total, 6 unused in this test).

UPDATE:
Ok, after testing one stick of new ram (2 gigs) and old ram (1 gig), It  came up as 2.8 gigs. I swapped out the new ram chips (alternating them),  and still got 2.8 GIGs of ram (Meaning that individually they're still  reading about 2 Gigs.) I then placed them all back in, and it showed as 6  gigs during the initial bios check during boot up. I didn't load bios  to update time/ect, and Ubuntu read 5.7 gigs (close enough) of RAM. Best  I can figure is it has to be something with the Bios setup, or happens  during a reboot. But all the RAM is reading as working.

I turned on Memory Mapping in the Bios, it went from 4.7 to 4.9 Gigs detected.

---

### Post by MoreOrLess on 2011-12-24
Do you have the IOMMU BIOS option enabled?

---

### Post by Stephan1864 on 2011-12-24
> **MoreOrLess said:**
> Do you have the IOMMU BIOS option enabled?

It was AGP Enabled. I disabled it, with on effect. I'll try setting it to the size of my video card.

---

### Post by Stephan1864 on 2011-12-24
> **Stephan1864 said:**
> It was AGP Enabled. I disabled it, with on effect. I'll try setting it to the size of my video card.

Ok, setting it to my Video card's memory size allowed the bios to detect all of the RAM. However, upon booting Linux, I got PANIC: early exception 00 rip 10:ffffffff815d84c0 error 0 cr2 f0496a

I'm thinking a memory error has popped up, but no idea. Any advice at this point would be useful, as I'm on a second PC to address this.

UPDATE:
Let it reboot twice, with AGP disabled, and it's back to 4.9 Gigs, but Linux is running again.

SOLVED: Ok, Set my IOMMU to 128, which seemed to have solved the problem. Not sure *why*, except that maybe the motherboard runs the RAM as 128 bit when it's on alternating DIMM slots, and of the same type and size. 64 MB gave an increase, but 128 has set me back to 5.9, which is close enough.

---

### Post by mörgæs on 2011-12-25
Please mark the thread 'solved' using 'thread tools'.

---

