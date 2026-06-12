---
title: "Opinions on my RAID plan"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by Kadin2048 on 2006-09-29
With the price of HDs where they are (around $40 for a decent 160GB on sale), I've been thinking maybe a RAID-5 array is the way to go for my storage requirements. I wanted to know what some other people think about my plan, lest I run off half-cocked.

I went through my junk box, and turned up a couple of IDE controllers:[LIST]
[*]Promise Tech. 20269 (rev. 2), 2-ch. IDE card[*]HighPoint RocketRAID 133, 2-ch. IDE card[/LIST]The latter is, I think, a "fakeraid" card...it's not real hardware RAID.

**First question**; has anyone ever used either of these cards? I've done the usual Googling and both of them seem to at lease have some reports of Linux compatibility. I plugged in the Promise, and it gets recognized by lspci as:```
0000:02:04.0 Mass storage controller: Promise Technology, Inc. 20269 (rev 02) (prog-if 85)
	Subsystem: Promise Technology, Inc.: Unknown device ad69
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (1000ns min, 4500ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin A routed to IRQ 169
	Region 0: I/O ports at 2460 [size=8]
	Region 1: I/O ports at 2454 [size=4]
	Region 2: I/O ports at 2458 [size=8]
	Region 3: I/O ports at 2450 [size=4]
	Region 4: I/O ports at 2440 [size=16]
	Region 5: Memory at e2000000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at 30000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 1
		Flags: PMEClk- DSI+ D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```What I'm worried about is whether I can use both of the cards <I>without</I> any RAID features in hardware, so they present the drives to Linux as just regular IDE volumes, so I can then do a software RAID-5 on them.

I was thinking I'd get 4 160GB drives, maybe two Seagates and two WD's, as I see them on sale.

This will be my first attempt at doing anything with RAID. What do people think of the plan so far? Is there anything obvious that I haven't thought of? I'm open to suggestions.

---

### Post by HAARP on 2006-09-29
Real Hardware RAID5 cards cost a fortune, I think both are Fake-Raid. Linux will see the real drives, no matter what those cards are set to.
I'd go for RAID10 with 4 drives

---

### Post by yota on 2006-09-29
Hi, you can do software raid with all block devices of your choice even at partition level.

see [http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
or use the ubuntu alternate install that lets you create RAID devices during the installation process.

I'm very happy with my software raid5+raid1+raid0 setup on 3 HD, it's something like this:
sda1+sdb1+sdc1 -> / 40GB raid5
sda2+sdb2+sdc2 -> 120GB /opt & /tmp raid0
sda3+sdb3 -> 1GB /boot raid1
sdc3 -> 1GB swap

all done without raid cards.
Just note that you have to boot from a "simple" or mirrored partition because grub does not support raid.

---

### Post by Kadin2048 on 2006-09-29
> **HAARP said:**
> Real Hardware RAID5 cards cost a fortune, I think both are Fake-Raid. Linux will see the real drives, no matter what those cards are set to.
I'd go for RAID10 with 4 drives

Thanks, Haarp.

I'm positive the cards are not hardware RAID-5.

However, I think that they might be quasi-fakeraid RAID-0 or 1.

I don't really understand fakeraid cards very well ... they ought to just be regular old IDE interface cards, shipped with some special drivers, right? So I ought to be able to just hook a drive up to each channel, and then do whatever kind of software RAID I want...?

My concern was that if the RocketRaid 133 was originally sold as a "RAID-0/1" card, can I use it just as a regular IDE interface? From a hardware perspective, I want to *not* use it as a RAID card.

And why do you recommend RAID 10 versus RAID 5?

---

### Post by HAARP on 2006-10-01
Yup, FakeRAIDs are plain IDE cards with special (Windoze)drivers. It's possible to get their Fake-RAID to work with Linux, but it's slow. You can however use plain Linux-Software-RAID, which beats every Fake-Raid available.

Real RAID5 cards are so expensive because they compute parity with a onboard-chip. When using Software-5, your CPU has to do all this. The loss in performance may be small, but I would still use RAID10. It's faster than 5, won't put as much load on your CPU and still is redundant.

---

### Post by pwrstick on 2006-10-01
> **yota said:**
> 
I'm very happy with my software raid5+raid1+raid0 setup

That's pretty nifty Yota!  However, just as a technicality, you're describing your Raid setup as something that doesn't quite make sense when you put it all together as 5+1+0.  You're saying you have a Raid 5 that is mirrored and then striped, instead of describing 3 different raids running on one system.  :-D 

Moving on, another reason to go Raid 1 over 5 is that writes are much faster with Raid 1 since parity information isn't also being written.  However reads are supposed to be comprable.  That being said, I'm creating a Raid 5 system for myself but it is going to be a file server doing nothing but raid and samba, and of course ssh :D

---

### Post by Kadin2048 on 2006-10-02
> **HAARP said:**
> Real RAID5 cards are so expensive because they compute parity with a onboard-chip. When using Software-5, your CPU has to do all this. The loss in performance may be small, but I would still use RAID10. It's faster than 5, won't put as much load on your CPU and still is redundant.

This computer normally has between 95-99% of its cycles idle anyway (I run Boinc on it in its spare time) so I'm not totally concerned about the overhead as long as it's minor, I'm more concerned about integrity and survivability of the data. And cost per MB.

Just to be sure we're on the same page, a RAID 10 would be a "stripe of mirrors," correct? Where you have two mirrored sets, and then stripe between them? So that the striping doubles your risk of failure, but the mirroring halves it, so you're left with about the same risk of the whole system failing as a single drive failing, right?  And the capacity would be 2x the smallest drive.

> **pwrstick said:**
> Moving on, another reason to go Raid 1 over 5 is that writes are much faster with Raid 1 since parity information isn't also being written.  However reads are supposed to be comprable.  That being said, I'm creating a Raid 5 system for myself but it is going to be a file server doing nothing but raid and samba, and of course ssh :D

This seems a little odd to me. Wouldn't the write speed be the same as a write to a single un-RAIDed drive? It seems like the bottleneck in any system these days would be the drive itself, and not the data manipulation beforehand -- since processors and the data busses are so much faster than the drive mechanisms. I'll take your word on it, though, since I've never played with it.

It seems like reading off of a mirrored configuration would be fast, though, since it can read from the drives just like it can read from stripes (not sure if the systems actually do this). In theory, you could read one block off of one drive in the mirrored set, while reading the next block in the file off of the other drive, and then leapfrog through the blocks. That would double the read speed.

Anyway, the reason I was considering RAID5 is that it looked like a good combination between striping and mirroring, but I'd never really considered how it would stack up to a RAID10 configuration. If anyone has a source for some hard numbers that would compare the size overhead and performance and redundancy requirements of 10 vs. 5, I guess I have some thinking to do.

---

### Post by mgmiller on 2006-10-02
Here is a good site for a lot of info on linux raid compatibility and which cards are fake or real:
[http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")

My experience has only been with RAID 1, but it has saved data many times when 1 drive in the array fails.

A reasonably priced card is the 3ware 8006-2LP 2-port which is only about US $124 but is real hardware raid, and has great linux support.

---

### Post by HAARP on 2006-10-02
> **Kadin2048 said:**
> ust to be sure we're on the same page, a RAID 10 would be a "stripe of mirrors," correct? Where you have two mirrored sets, and then stripe between them? So that the striping doubles your risk of failure, but the mirroring halves it, so you're left with about the same risk of the whole system failing as a single drive failing, right?  And the capacity would be 2x the smallest drive.

It's 0 (striping) + 1 (mirroring) with min. 4 drives, that's right
But you're wrong. Striping adds speed, and mirroring adds redundancy. Imagine having a single 0-array and adding another 0-array that mirrors the first one. It's redundant.
Capacity is 2x smalles drive size, yes.

---

