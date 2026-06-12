---
title: "Building my first tower PC"
date: 2013-03-06
forum: Hardware
---

### Post by Joreus on 2013-03-06
Hey everyone,

I'm looking to build a PC tower on my own and I'm only going to run Linux on it. Ubuntu 12.04.2 (KDE/XFCE in particular). This will be my first time having done this, so any advice or tips you can give would be most appreciated.

My current tower is becoming a little dated and is starting to periodically freeze. I'm going to be cannibalizing the DVD+/-RW drive and both HD drives. So that should cut down a little on my expenses.

I have some parts that I have been looking at already:
CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116504](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116504)
MOBO: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131819](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131819)
CPU Fan: [http://www.newegg.com/Product/Product.aspx?Item=N82E16835103099](http://www.newegg.com/Product/Product.aspx?Item=N82E16835103099)

As far as I can tell, all of these components work under 12.04.2. (I picked Intel only because I heard they're a little more Linux friendly, but I'm flexible). I initially considered an i3 and I'm sure it would serve just as well, my thoughts were that the i5 would make a better long term investment.

I will NOT be using this PC for gaming (per orders from wife), though I would still like the system to handle graphics without a hitch and look decent.

May decide to do this right away or at some point in the future: a SSD. It does not have to be large and would only house the OS and preferably I'd have at least one HD installed for all of my files and backup.

What I need: power supply, RAM, case and possibly a different CPU fan. I'd prefer a system that would be quiet and low power.

I have about $800 to spend in total. I humbly ask for any suggestions and/or corrections.

---

### Post by prodigy_ on 2013-03-06
EVO is supposed to be quiet AFAIK. i5 integrated gfx should be good enough if you're not gaming. As for RAM - buy 8GB of 1600Mhz DDR3 as sandy bridge/ivy bridge don't really benefit from higher RAM freqs.

SSD is a must. ;) Once you try you won't want to go back. HDDs are still good for data but you really want SSD for your system partition.

---

### Post by drmrgd on 2013-03-06
I agree pretty well with the above comments, and just wanted to add to make sure you get a decent power supply.  You don't need anything massive, but get a 80plus certified unit, which will save power and you money in the long run.  

Also, I would recommend getting new hard drives for the system now.  Whether you go with SSDs or HDs is up to you.  But, unless the drives you have now are very new, they're more likely to fail than brand new ones, and now's as good a time as any to get fresh drives in there that (hopefully) you won't have to worry about for a while.

---

### Post by Joreus on 2013-03-06
@drmrgd: Does this seem good? Or should I be looking for something with a higher wattage?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026)

@prodigy_: Yes, that's what I'm looking to do. I know a few people that changed over to SSD's and I was sold after I saw them. Like I said, I only would want a small one for the OS and programs, but the slower drives for any other data. Any recommendations on the SSD's? I've seen Crucial being mentioned in other threads.

Edit: What about changing the i5 chip? Maybe drop the integrated grahics in the MOBO and CPU and get an average graphics card?
Edit2: Is there a substantial difference between the UEFI and non-UEFI MOBOs? Will it be more of a headache to use a UEFI board?

---

### Post by prodigy_ on 2013-03-06
Samsung 840 and OCZ Vertex 4 seem to be the favorites. I bought Intel 520 and can't say anything bad about it but still I probably overpaid (Vertex 4 offers the same, if not better, performance and comes with the same 5-year warranty).

I tried i5 integrated gfx at work and it's very good. Keep in mind that Intel provides open source drivers unlike nVidia or AMD. And it's quite annoying to update binary drivers manually after each kernel update.

---

### Post by oldfred on 2013-03-06
All new motherboards are UEFI, but have a CSM or BIOS compatibility module or add-in. Since you do not have Windows 8 pre-installed you will not have the issues of secure boot.
You will want to use gpt partitioning whether UEFI or BIOS as Ubuntu works with gpt either way. Windows has to have UEFI to boot from a gpt partitioned drive.
 GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)


Not Linux but some idea of different builds.
[http://www.tomshardware.com/reviews/build-a-pc-overclock-benchmark,3441.html](http://www.tomshardware.com/reviews/build-a-pc-overclock-benchmark,3441.html)

If you look at the chart on the last page it shows approximately how cards compare. You can see if a card is much better than Intel 4000.
[http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html](http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html)

---

### Post by drmrgd on 2013-03-06
> **Joreus said:**
> @drmrgd: Does this seem good? Or should I be looking for something with a higher wattage?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139026)

@prodigy_: Yes, that's what I'm looking to do. I know a few people that changed over to SSD's and I was sold after I saw them. Like I said, I only would want a small one for the OS and programs, but the slower drives for any other data. Any recommendations on the SSD's? I've seen Crucial being mentioned in other threads.

Edit: What about changing the i5 chip? Maybe drop the integrated grahics in the MOBO and CPU and get an average graphics card?
Edit2: Is there a substantial difference between the UEFI and non-UEFI MOBOs? Will it be more of a headache to use a UEFI board?

Personally, I think 430 Watts is on the lean side.  I know I've seen a lot of discussion and argument over how big one should go.  To me, though, I think less than 600 Watts is a little too small.  Without a dedicated GPU, and with an SSD (if you decide to go either or both of those routes), I guess the power draw will be less.  So, maybe now a days less than 600 Watts is OK?

I have both the Samsung 840 (250 GB) and a Crucial (128 GB) SSD in my computer, and they both seem to perform very well.  Haven't had any problems with either so far.  At work I have an older Samsung SSD (don't know the model but I remember it's 500GB), and that one seems to work quite well too (and I do tend to 'abuse' that one with a lot of reading and writing large files!).  I think the Samsung gets better ratings, but the price is higher.  Not sure if that helps...

I'm not sure I necessarily agree with prodigy on the drivers for the GPUs.  I don't know much about the AMD cards as I prefer the Nvidia cards, but the open source Noveau driver from the Ubuntu repos seems to drive my card just fine.  I just did just swap out that driver for the proprietary one a few weeks ago (and prodigy's definitely right that it's a bit of a pain to have to do that potentially every time you update the kernel), but I don't really notice any bit of difference.  To be honest, I can't quite remember now what motivated me to switch to the proprietary driver now that I think about it!

---

### Post by andrew.46 on 2013-03-07
Don't forget to get the nicest case you can afford, it will make both the initial build and then later upgrades a much nicer experience :)

---

### Post by lisati on 2013-03-07
*Thread moved to **Hardware**.*

---

