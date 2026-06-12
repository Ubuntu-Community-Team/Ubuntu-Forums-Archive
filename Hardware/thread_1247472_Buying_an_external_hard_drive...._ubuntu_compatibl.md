---
title: "Buying an external hard drive.... ubuntu compatible"
date: 2009-08-23
forum: Hardware
---

### Post by arashiko28 on 2009-08-23
I want to buy a 1TB external portable hard drive, now, I have seen many brands having compatibility issues.

My 3 main choices are:

-Western Digital
-Iomega
-Seagate

The three of them compete in price and size, and both are importants, but taking into account that I don't have and don't plan to buy windows (EVER!!!), there is also the compatibility issue. So any recommendations are welcomed and thanked.

PD: It's a tough call when it comes to design, so low price and smaller, the better.

---

### Post by acankat on 2009-08-23
You should go for the WD, I've been using WD disks since the first 10.000 RPM raptor release and using a 1 TB caviar black at the moment. WD disks have always been good performers and reliable pieces.

Never used an external one though. Bu inside the box, they should be same disks after all.

---

### Post by recluce on 2009-08-23
I have connected all of the combinations below without a hitch:

- Icy Box with Hitachi 500 GB drive via USB
- No Name Box with ages old IBM Travelstar 30 GB drive via USB
- TrekStor 500 GB external box (Samsung drive) via USB
- Star Tech Dock with WD Caviar Black 1 TB and other SATA drives both via USB and eSATA

So I would assume that almost any combination should work fine, as long as you stay away from "Bells & Whistles" boxes that offer features like "One Button Backup" or other weird, Windows only features.

And yes, WD Caviar Black 1 TB drives seem to have just about the best reputation of the 1 TB bunch.

---

### Post by arashiko28 on 2009-08-24
I haven't seen those caviar black disks, WD has on it's web page the my book for the desktop drives and the my essential for the portable drives.:confused:

---

### Post by recluce on 2009-08-24
> **arashiko28 said:**
> I haven't seen those caviar black disks, WD has on it's web page the my book for the desktop drives and the my essential for the portable drives.:confused:

I never buy a pre-assembled external drive, since you never know what actual drive is inside.

So the WD Caviar Black is one of the better "internal" drives, which I would combine with an enclosure that gets good reviews either on this forum or on newegg.com. 

While I am at it, I would get an enclosure that supports eSATA, since this will be three times faster than USB 2.

---

### Post by gamemaniac7 on 2009-08-25
I just wanted to go for an external hard drive, brand is not the problem but I am just wondering, will it make data transfer slow? I am really concerned about the speed of the external drive and in that respect how much is the difference between the internal and the external hard drive?

---

### Post by recluce on 2009-08-25
> **gamemaniac7 said:**
> I just wanted to go for an external hard drive, brand is not the problem but I am just wondering, will it make data transfer slow? I am really concerned about the speed of the external drive and in that respect how much is the difference between the internal and the external hard drive?

Yes, there may be quite a difference if you connect through USB.

For my internal drive (SATA, laptop drive): ~60 MB/sec
For my USB drives (any and all): 17 to 19 MB/sec
For my external eSATA drive: ~65 MB/sec

The above is speed reported by Ubuntu on large file copies, not some arcane benchmark.

Facit: if you want speed, get an external eSATA enclosure and a controller card for your laptop, if you haven't got a real modern laptop with eSATA build in.

---

### Post by arashiko28 on 2009-08-26
Tucking a usb converter for an eSata cable looks kind of tricky, at the end won't go faster than the usb can support, that's my guess. Any way, I did thought of buying the disk apart and the enclosure, but for the portables there are not many trustworthy offers for 1TB drives. I do have firewire port 1394... I do trust on some brands, and have tested the my book HD, but to test a 1TB drive... well... my testings consist on filling the disk at it's full capacity, calculate the transfer time and unplugging, when I plug back, random testing the files copied, this it's a good way to detect fakes that promise a size and are way smaller, like a friend of mine who bought a 32GB pen drive, turns out that after 1GB, when you plug it back in, all the data gets corrupted, except what was copied on the first GB :(

---

### Post by Rifester on 2009-08-26
I have a Western Digital 1TB external hard drive.  It has worked without flaw on Ubuntu.

---

### Post by Donalb on 2009-08-27
The Iomega drive is almost 100% certainly a seagate drive (ex-Iomega employee, also ex-Seagate employee).
I would go with the original Seagate drive if cheaper, the Iomega one if not.
I would personally keep away from WD as their DPPM reliability is bit less (worked as OEM engineer so I had a good idea of the real world quality of the various vendors).
All drives will work fine in 'buntu.

---

### Post by recluce on 2009-08-27
> **arashiko28 said:**
> Tucking a usb converter for an eSata cable looks kind of tricky, at the end won't go faster than the usb can support, that's my guess. 

I am really not sure what you want to do here. What I proposed was:

eSATA controller card in your Express Card slot. eSATA/USB combo enclosure connected to that. If at your main machine, use the eSATA connection for top speed. If elsewhere, use the USB for compatibility.

No need for an USB converter cable. :confused:

---

### Post by gamemaniac7 on 2009-08-31
This was useful information Recluce. Thanks for answering. Are the latest laptops coming with eSATA hard drive built in.

---

### Post by recluce on 2009-08-31
> **gamemaniac7 said:**
> This was useful information Recluce. Thanks for answering. Are the latest laptops coming with eSATA hard drive built in.

Most laptops have had **internal** SATA drives for at least two years, some longer. The external SATA connector (hence **e**SATA) is still fairly rare and only to be found on recent, higher-end laptops. However, if you have an Express Card slot, you can just buy a controller card for a few bucks.

---

### Post by gamemaniac7 on 2009-09-04
Thanks Recluce for answering my query. I was really confused about extra SATA connector. If you could send me a link where some good descriptive information is available, it would be helpful.

---

### Post by recluce on 2009-09-04
> **gamemaniac7 said:**
> Thanks Recluce for answering my query. I was really confused about extra SATA connector. If you could send me a link where some good descriptive information is available, it would be helpful.

This page has details about the card I use and know to work with Ubuntu:

[http://www.siig.com/ViewProduct.aspx?pn=SC-SAE512-S1](http://www.siig.com/ViewProduct.aspx?pn=SC-SAE512-S1)


And, the Wikipedia article is not bad:

[http://en.wikipedia.org/wiki/ESATA#External_SATA](http://en.wikipedia.org/wiki/ESATA#External_SATA)


This takes care of the controller side. For the enclosure, eSATA is very easy. Any eSATA enclosure should do. If portability is not too important, I find the harddisk docks very practical. You connect the "naked" drive into the dock like a slice of toast - and it can be ejected this way! This makes swapping multiple drives a breeze.

If you need a portable enclosure, a dual USB/eSATA would be best - in this way you still can connect your drive to computers that have no eSATA

---

### Post by gamemaniac7 on 2009-09-05
This was descriptive information Recluce and thanks for replying. You seemed to be well informed with these things which is a good. I won't mind asking something else too if you don't mind answering. There is a word going around about Solid State Drives. Can you guess in what time Solid Sate Drives will be a common feature in the laptops and if you want to buy a SSD now, how much it can cost you?

---

### Post by recluce on 2009-09-06
> **gamemaniac7 said:**
> This was descriptive information Recluce and thanks for replying. You seemed to be well informed with these things which is a good. I won't mind asking something else too if you don't mind answering. There is a word going around about Solid State Drives. Can you guess in what time Solid Sate Drives will be a common feature in the laptops and if you want to buy a SSD now, how much it can cost you?

I would say that SSD drives are a common feature today on high-end notebooks. I personally have no experience with SSD notebook drives as yet, as they are still quite pricy. I cannot direct you to any sources, since I do not know where on this planet you are located.

Also, many SSD drives seem to be performing badly, so you will have to read up on whatever drive takes your fancy. I have heard good things about some models from Intel and OCZ, so that might give you a point to start.

As a common feature? It will be a trickle down from high-end to mid-market to mass market. I would guess that in about 2 to 3 years, only cheaper consumer notebooks will use regular HDs as standard equipment.

But let's wait and see...

---

### Post by gamemaniac7 on 2009-09-07
I was a little bit skeptical about SSD. Someone was also saying that SSD has finite erasing potential. I don't know how much truth is there in this fact. What do you say about that?

---

### Post by recluce on 2009-09-07
> **gamemaniac7 said:**
> I was a little bit skeptical about SSD. Someone was also saying that SSD has finite erasing potential. I don't know how much truth is there in this fact. What do you say about that?

This is true, but all drives implement an internal wear management. In other words, they "swap" memory cells around, mapping them to different blocks of the disk, to average wear over the whole drive. Raw writes to a single cell before failure go to the 100,000s, if memory serves.

Once more, much depends on the quality of the SSD drive.

---

### Post by gamemaniac7 on 2009-09-08
As you are talking about an Internal Wear Management which I hardly know about. Is there any Internal Wear Management in the conventional hard drives as well. While we are talking about infinite erasing potential I just wanted to know what is the erasing potential of conventional hard drive?

---

### Post by recluce on 2009-09-08
> **gamemaniac7 said:**
> As you are talking about an Internal Wear Management which I hardly know about. Is there any Internal Wear Management in the conventional hard drives as well. While we are talking about infinite erasing potential I just wanted to know what is the erasing potential of conventional hard drive?

I am not aware of design limits or life expectancy of conventional drives being expressed in terms of write/erase cycles. I am sure that there is a limit, but it just may not be relevant compared to other factors that limit useful service life of a drive.

And yes, all drives (except for ancient IDE drives) do have a defect management (not a wear management). If a sector becomes unreliable, the drive will map one of the reserved "spare sectors" to that sector instead. This does not mean that you will notice any errors or problems with the drive.

In my experience, you will see a drive occasionally that has a few remapped sectors - and that is not a problem. Most drives, however, tend to have either no remapped sectors at all or lots of them and a quickly growing number - this indicates a drive that is failing.

Use smartmontools to find out about the health of your drives (does not work on most USB bridges, however).

---

### Post by gamemaniac7 on 2009-09-09
You appropriately used the word "Ancient IDE Drives". I was just thinking about buying an external hard drive. The configuration I am looking for is at least 160 GB capacity at 7200 RPM, data transfer has to be fast. It could be of any brand but has to be superior in quality. Can you suggest one or two of your choice that you have seen recently?

---

### Post by recluce on 2009-09-09
> **gamemaniac7 said:**
> You appropriately used the word "Ancient IDE Drives". I was just thinking about buying an external hard drive. The configuration I am looking for is at least 160 GB capacity at 7200 RPM, data transfer has to be fast. It could be of any brand but has to be superior in quality. Can you suggest one or two of your choice that you have seen recently?

Not really, since you hear conflicting things about the most popular, preassembled drives like WD and Seagate. Also, if you go USB, 7200 rpm makes no sense, since the bottleneck is the USB port. I would buy enclosure and drive separately - and go through 5 minutes of assembly.

If you want to buy a preassembled external drive, I suggest you read through the customer comments on newegg.com, this should give you some idea about reliability.

---

### Post by gamemaniac7 on 2009-09-10
I did check the Newegg site suggested by you but what I find it is still better to get your views personally as your replies are simple and straight and therefor things don't look complicated. As you were saying that USB is the bottleneck and 7200RPM drive hardly matters so in that context I just wanted to know how much is the difference between 5400 RPM HDD and 7200 RPM HDD in terms of data transfer rates for internal hard drives not external?

---

