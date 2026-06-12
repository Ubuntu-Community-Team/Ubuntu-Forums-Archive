---
title: "DELL Inspiron E1505 RAM installation queries"
date: 2016-01-07
forum: Hardware
---

### Post by argonvegell on 2016-01-07
**DELL INSPIRON E1505**
**Operating System:** Windows XP Professional 32-bit SP2
**CPU:** Intel Mobile Core 2 Duo T5500 @ 1.66GHz, Merom 65nm Technology
**RAM:** 1GB Dual-Channel DDR2 @ 266MHz (4-4-4-12)
**Motherboard:** Dell Inc. 0KD882 (Microprocessor)
**Graphics:** Plug and Play Monitor (1280x800@60Hz), Intel Mobile Intel 945GM Express Chipset Family (Dell)
**Storage:** 110GB Western Digital WDC WD1200BEVS-75LAT0 (SATA)
**Optical Drives:** TSSTcorp DVD+-RW TS-L632D
**Audio:** SigmaTel High Definition Audio CODEC
  
 E1505's maximum RAM is 2GB, and can only accept DDR2 RAM sticks, and  after searching lots of computer stores, the only DDR2 for Laptops I  found is a one 2GB DDR2 RAM stick, my question is, can E1505 handle one  2GB DDR2 RAM stick on one slot, while the other slot is empty? If not, I guess I'll have to stick with my current specs then, unfortunately ordering online is not an option.

I'm planning on installing Xubuntu 14.04, and I heard that with my  current specs, Xubuntu 14.04 can still run pretty smoothly, is this true?

---

### Post by Dennis N on 2016-01-07
It can use a 2 gB module according to the 1505/6400 user manual. The maximum memory is also 2 gB, so one will do it:

Memory
Memory module connector         two SODIMM connectors
Memory module capacities         256 MB, 512 MB, 1 GB, and 2 GB
Memory type                     1.8-V SODIMM DDR-2
Minimum memory                256 MB
Maximum memory                2 GB

I have a Dell 1505 N, which is similar, but came with Ubuntu pre-installed by Dell. Mine has a Pentium dual core T2080 processor and I use Xubuntu 14.04 on it currently. It performs well. I have 2 x 1gB memory sticks.

---

### Post by argonvegell on 2016-01-07
> **Dennis N said:**
> It can use a 2 gB module according to the 1505/6400 user manual. The maximum memory is also 2 gB, so one will do it:

Memory
Memory module connector         two SODIMM connectors
Memory module capacities         256 MB, 512 MB, 1 GB, and 2 GB
Memory type                     1.8-V SODIMM DDR-2
Minimum memory                256 MB
Maximum memory                2 GB

I have a Dell 1505 N, which is similar, but came with Ubuntu pre-installed by Dell. Mine has a Pentium dual core T2080 processor and I use Xubuntu 14.04 on it currently. It performs well. I have 2 x 1gB memory sticks.

Wait a minute, you were able to push past the RAM limit? 2 x 1GB = 3GB?

---

### Post by Dennis N on 2016-01-07
No, 2 x 1 gB is short for two 1 gB memory sticks = 2 gB total.

---

### Post by weatherman2 on 2016-01-07
I have a couple of E1505s - used by family members.  2GB is the max RAM, but I'm not sure one 2GB stick would work - and even so, it would not be dual channel so might be slightly slower than two 1GB sticks.  It should be easy to find 1GB DDR2 sticks on eBay.  PC2-3200 (DDR2, not DDR) will work but PC2-4200 (or 4300) or PC2-5300 would be a little faster.

I'm using Ubuntu 12.04 on mine - with Gnome Fallback (aka "classic") with Metacity on mine - very fast for such old hardware.

---

### Post by argonvegell on 2016-01-07
> **Dennis N said:**
> No, 2 x 1 gB is short for two 1 gB memory sticks = 2 gB total.

Thanks for the clarity.

> **weatherman2 said:**
> I have a couple of E1505s - used by family  members.  2GB is the max RAM, but I'm not sure one 2GB stick would work -  and even so, it would not be dual channel so might be slightly slower  than two 1GB sticks.  It should be easy to find 1GB DDR2 sticks on eBay.   PC2-3200 (DDR2, not DDR) will work but PC2-4200 (or 4300) or PC2-5300  would be a little faster.

I'm using Ubuntu 12.04 on mine - with Gnome Fallback (aka "classic")  with Metacity on mine - very fast for such old hardware.

Unfortunately I couldn't find two 1GB DDR2 memory sticks and ordering online isn't really an option, I got burned buying computer supplies online, so I prefer to touch, feel and test the item personally.

My question, can Xubuntu 14.04 can still run pretty smoothly on my current specs?

---

### Post by Dennis N on 2016-01-07
> but I'm not sure one 2GB stick would work

But, if it can use a 2gB module (as the user manual says), how else could that be possible without leaving the second slot empty?

> My question, can Xubuntu 14.04 can still run pretty smoothly on my current specs?

Well, "pretty smoothly" is subjective, but I have always been satisfied with how it has performed. I have the same graphics, and have no complaints.

---

### Post by Dennis N on 2016-01-07
Just to add, I put in an SSD about 14 months ago, and that was a very worthwhile upgrade.

---

### Post by weatherman2 on 2016-01-07
> **argonvegell said:**
> Unfortunately I couldn't find two 1GB DDR2 memory sticks and ordering online isn't really an option, I got burned buying computer supplies online, so I prefer to touch, feel and test the item personally.

2x1GB PC2-5300 or PC2-4200 is ridiculously cheap online (used) - here in the US, anyway.    I just found a set of two for $5.99 USD shipped.  That's not exactly a big risk.  I've bought lots of used parts on eBay and in rare cases when the part was bad, the seller, eager to avoid negative feedback, has always been accommodating.  But you might not live in the US so you may not have access to such cheap prices.

---

### Post by argonvegell on 2016-01-07
> **Dennis N said:**
> But, if it can use a 2gB module (as the user manual says), how else could that be possible without leaving the second slot empty?



Well, "pretty smoothly" is subjective, but I have always been satisfied with how it has performed. I have the same graphics, and have no complaints.

I guess that's the jiff of my inquiry, can E1505 handle only one 2GB DDR2 RAM stick? According to the manual, it can handle it, but according to weatherman2 2GB on a single slot might be slower, so I await second and third opinions.

> **Dennis N said:**
> Just to add, I put in an SSD about 14 months ago, and that was a very worthwhile upgrade.

I'd love to get a SSD, but it's too expensive for us at the moment.

---

### Post by weatherman2 on 2016-01-07
> **argonvegell said:**
> I guess that's the jiff of my inquiry, can E1505 handle only one 2GB DDR2 RAM stick? According to the manual, it can handle it, but according to weatherman2 2GB on a single slot might be slower, so I await second and third opinions.

It WILL be slower with one 2GB stick vs two 1GB sticks - but the question is, how much slower?  Slow enough to notice?  Maybe not.  I would not hesitate to use one 2GB stick if that was my cheapest option.  It would not be my cheapest option (see above) but perhaps it is yours.

---

### Post by argonvegell on 2016-01-07
> **weatherman2 said:**
> It WILL be slower with one 2GB stick vs two 1GB sticks - but the question is, how much slower?  Slow enough to notice?  Maybe not.  I would not hesitate to use one 2GB stick if that was my cheapest option.  It would not be my cheapest option (see above) but perhaps it is yours.

Well, there a still a couple of used computer supplies stores that I haven't tried yet, it's because I couldn't get them on the phone to inquire, no one was answering, I've done business with them in the past, so I'll go there personally and see if they have two 1GB RAM sticks, but if not, I guess I'll have to settle with what I've found, one 2GB RAM stick.

---

### Post by Yellow Pasque on 2016-01-08
> **weatherman2 said:**
> It WILL be slower with one 2GB stick vs two 1GB sticks - but the question is, how much slower?  Slow enough to notice?  Maybe not.  I would not hesitate to use one 2GB stick if that was my cheapest option.  It would not be my cheapest option (see above) but perhaps it is yours.

If it came down to it, I think I'd rather have 2GB RAM than dual-channel boost.
Still, it should be easy to find 2 SO-DIMMS of DDR2-667 (aka PC2-5300) if you look hard enough.

---

### Post by argonvegell on 2016-01-08
**UPDATE**
No luck in getting two 1GB DDR2 RAM sticks, and turns out that one 2GB DDR2 RAM stick is defective and there no more in stock, so I'm stuck with 1GB Dual-Channel DDR2 @ 266MHz
110GB WD SATA Hard drive has failed, unfortunately, SSD isn't an option, too expensive, so I will be purchasing a 500GB WD SATA Hard drive.

How well does Xubuntu 14.04 run on a 500GB WD SATA Hard drive and 1GB Dual-Channel DDR2 @ 266MHz?
And would Xubuntu 16.04 be able to run on these specs?

---

### Post by Dennis N on 2016-01-08
Memory usage after boot is 191 mB (no user applications running) with Xubuntu 14.04. After starting Firefox, 325 mB. 

There should be no problem with any SATA 2.5" disk drive.
As to the memory, Kingston says it uses either DDR2-533 or DDR2-667. Mine has DDR2-533. Will slower work??
Kingston sells new 1 gB DDR2-667 modules for $16.60. They don't make the 533 anymore, apparently. At least they guarantee it.

[Link to Kingston Web Page]("http://www.kingston.com/us/memory/search/Default.aspx?DeviceType=3&Mfr=DEL&Line=Inspiron&Model=27960&Description=Kingston_System_Specific_Memory_for_Dell_Inspiron_E1505")

---

### Post by Yellow Pasque on 2016-01-08
Crucial sells a 2x1GB kit for $28. It's a bit pricey but Crucial's a reputable vendor that also guarantees compatibility. [http://www.crucial.com/usa/en/inspiron-e1505/CT541126](http://www.crucial.com/usa/en/inspiron-e1505/CT541126)

---

### Post by Dennis N on 2016-01-08
> Crucial's a reputable vendor that also guarantees compatibility

I agree, and a better deal! I have used Crucial memory in my computers as well; and the SSD I bought for that Dell 1505 is a Crucial SSD.

---

### Post by weatherman2 on 2016-01-08
Personally, I wouldn't invest in new RAM for a ten year old laptop.  I've had great luck with used parts.

My friend put an SSD in his 6400 (E1505) and did get a noticeable speed boost, but this will be limited because I think The E1505/6400 is only SATA I (1.5Gbps) so you won't get nearly the full benefit from an SSD you'd get in a SATA II or SATA III laptop.  The biggest benefit would probably be startup and shutdown time, but this is already pretty fast with Ubuntu.

---

