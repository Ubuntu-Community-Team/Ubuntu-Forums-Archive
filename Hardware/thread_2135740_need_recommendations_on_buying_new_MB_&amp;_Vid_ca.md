---
title: "need recommendations on buying new MB &amp; Vid card"
date: 2013-04-15
forum: Hardware
---

### Post by s1baker on 2013-04-15
Hi,
After nearly 7 years, my old trusty desktop bit the dust.
Now I am in the market for a new desktop so I need some recommendations
on a good MB & Vid card that will work with Ubuntu ( specifically Xubuntu ).

 I want this to be AMD ( not Intel ) and I want 8 gigs ram to start, eventually will expand to 16 gigs.
 I tend to use a computer until it falls apart, so I plan on keeping it a long time, therefore I would like
something more toward the high end, with the idea that I might be able to upgrade it as long as possible,
I just don't want to go overboard on the price and get anything super-high end.
Also, I run 12.04 LTS

Thanks for any info.

---

### Post by CatKiller on 2013-04-15
I find the Ars Technica System Guides a good place to start.

---

### Post by kurt18947 on 2013-04-15
Historically, ATI/AMD video has been a less smooth ride on linux than has Intel or Nvidia.  I've read posts that indicate AMD is doing more with video drivers etc. but I have no first hand experience.  I have a 2009ish Gigabyte M.B. w/AthlonII X2 processor so not a up-to-date machine.  It works fine except for a BIOS that doesn't like to boot live USBs unless they were formatted to FAT32 with Windows.  Live USBs formatted to FAT32 using gparted boot fine on 2 Thinkpads and one older AMD/Gigabyte system so it appears to be just that one BIOS version.

---

### Post by s1baker on 2013-04-15
I would not mind going with Nvidia but wasn't Nvidia the one that Linus was ragging on a while back because they wern't supporting Linux like they should?

---

### Post by s1baker on 2013-04-15
what about these guys?

motherboard:
```
Gigabyte Ultra Durable 4 Classic GA-78LMT-USB3 Desktop Motherboard - AMD 760G Chipset - Socket AM3+
```

cpu:
```
AMD Quad-Core Processor FX-4100 (3.6 GHz) AM3+
```


video card:
```
XFX HD-645X-ZQH2 Radeon HD 6450 625 MHz Core - 1 GB 
```
except I don't see the 6450 listed here for 12.04:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by andrew.46 on 2013-04-16
I have recently built the computer that I am typing this post on and I think you are on a good road looking for an AMD chip! This one has the new AMD FX(tm)-8350 Eight-Core Processor running on an Asus board. These chips are not that expensive and well worth a look at. Disregard almost all of the negative press about the 8 core chips, this one screams along and the price was definitely right. I went with NVidia for graphics and although there has been some instability recently with the closed source drivers I would still recommend NVidia graphics...

---

### Post by kurt18947 on 2013-04-16
> **andrew.46 said:**
> I have recently built the computer that I am typing this post on and I think you are on a good road looking for an AMD chip! This one has the new AMD FX(tm)-8350 Eight-Core Processor running on an Asus board. These chips are not that expensive and well worth a look at. Disregard almost all of the negative press about the 8 core chips, this one screams along and the price was definitely right. I went with NVidia for graphics and although there has been some instability recently with the closed source drivers I would still recommend NVidia graphics...

I haven't really kept up with the Intel vs. AMD processor debate but as of a couple years ago, Intel processors would benchmark a lot better than AMD.  The reason, at least in part is that individual Intel cores were faster, AMD would offer more cores for the same $.  Windows software was unable to effectively utilize more than 2 cores so a dual core processor with faster cores might benchmark better than a quad core AMD CPU, 2 of whose cores were nearly idle.  I don't know if Linux is better in that regard or not.  Another case of it being wise to look at benchmarks with a skeptical eye.

---

### Post by WTF_Shelley on 2013-04-16
I just built a new ubuntu desktop with a i5 3570k and 8 gig of ram, the cpu has a intel hd4000 gpu built into it and is supported with open source drivers. so hopefully no gpu shennigans

---

