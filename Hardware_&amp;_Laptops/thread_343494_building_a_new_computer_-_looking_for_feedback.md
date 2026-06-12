---
title: "building a new computer - looking for feedback"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by jrib on 2007-01-21
Okay, this is the first time I'm building and would appreciate any feedback you can give me on the following setup:

**CPU: **
[ AMD Athlon 64 X2 3800+(65W) Windsor 2.0GHz Socket AM2 Processor Model ADO3800CUBOX - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16819103733")

**Motherboard:**
[ ASUS M2N-SLI Deluxe Socket AM2 NVIDIA nForce 570 SLI MCP ATX AMD Motherboard - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16813131013")

**Video Card:**
[ GIGABYTE GV-NX76T256D-RH GeForce 7600GT 256MB GDDR3 PCI Express x16 Silent Pipe II, Lead Free Video Card - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16814125025")

**PSU:**
[ SeaSonic S12-430 ATX12V 430W Power Supply - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16817151023")

**RAM:**
[ CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model TWIN2X2048-6400C4 - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16820145034")

**DVD:**
[ LITE-ON 20X DVD±R DVD Burner included extra White bezel, with 12X DVD-RAM Write Black IDE Model LH-20A1P-186 - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16827106050")

**Hard Drive:**
[ Western Digital Caviar SE16 WD2500KS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM]("http://www.newegg.com/Product/Product.asp?item=N82E16822144701")

**Case:**
[ LIAN LI PC-61 USB Black Aluminum ATX Mid Tower Computer Case - Retail]("http://www.newegg.com/Product/Product.asp?item=N82E16811112025")

Total is about $1000 US before rebates at newegg but I still have to shop around once I decide on the parts so hopefully that will drop a little bit.

Anything you would change if you were building this?  The conroes are nice but too expensive so I went with the amd and I hope that the fact that it's AM2 will leave plenty of upgrade options for the future.

---

### Post by skewray on 2007-01-23
It is a lot cheaper to buy an entire system that to build out of parts.  I always build out of parts also, but not to save money.  I would suggest two hard drives, and then RAID-1 the partitions that you really don't want to lose.  This prevents the sick feeling you get after a disk crash.

---

### Post by robenroute on 2007-01-23
> **skewray said:**
> It is a lot cheaper to buy an entire system that to build out of parts.  I always build out of parts also, but not to save money.

Agreed. However, like you mentioned, building your own increases the chances of all your components (if picked properly) behaving nicely when running Linux. This should be high priority.

> **skewray said:**
> I would suggest two hard drives, and then RAID-1 the partitions that you really don't want to lose.  This prevents the sick feeling you get after a disk crash.

Yes, but proper RAID deployment often calls for proper hardware (separate RAID controller card); on-board RAID solutions aren't always troublefree.

Back to _jason: your system looks more than fine and should run without problems.

Have fun!

---

### Post by Josh1 on 2007-01-23
> **skewray said:**
> It is a lot cheaper to buy an entire system that to build out of parts.  I always build out of parts also, but not to save money.  I would suggest two hard drives, and then RAID-1 the partitions that you really don't want to lose.  This prevents the sick feeling you get after a disk crash.

OH Please don't make me laugh. Buying an entire system is overpriced and usually you can get the entire thing for hundreds sometimes even a grand less. :roll:

---

### Post by skewray on 2007-01-23
Use software RAID.  Of course, it isn't cear to me that Ubuntu supports this, since it won't recognize RAID partitions on already existing partitions, but you should be able to set it up after Ubuntu is installed.  Software RAID is often faster anyway.

---

### Post by zekopeko on 2007-01-23
i would change the processor and motherboard.

core 2 duo + MB for it, the rest looks good.

UPSSS!!! just read read the last line of your post.

but what is the price diffrence for Core 2 Duo 2Ghz and this AMD?

---

### Post by dannyboy79 on 2007-01-23
I actually just bought this DVD/RW Drive and it works awesome with Dapper; Optiarc DVD RW AD-7170A. I have used Nero Linux, Gnomebaker, and Nautilus Burning Thingy and all write great, it states it writing them at 8X but it does a full DVD, xbox iso game in about 5 mins.. DVD-RAM also writes at 12X as well. Here's a link. [http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=18307](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=18307)
I am only saying this because I can tell you for sure that this burner writes fine using TDK DVD+R from buy.com. 100 of them for around $25 is a steal! [http://www.buy.com/retail/product.asp?sku=201746002&loc=101&sp=1](http://www.buy.com/retail/product.asp?sku=201746002&loc=101&sp=1)

Also, you can get a WD 500GB Sata 300 drive from tigerdirect.com for 149.99 so why buy a 250 if you're going OEM, then buy from tigerdirect. [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2795126&Sku=TSD-500AAKS](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2795126&Sku=TSD-500AAKS)

i would also second the intel dual core.

---

### Post by robenroute on 2007-01-23
> **zekopeko said:**
> i would change the processor and motherboard.

core 2 duo + MB for it, the rest looks good.

UPSSS!!! just read read the last line of your post.

but what is the price diffrence for Core 2 Duo 2Ghz and this AMD?

Now, why would you change the CPU and motherboard? I reckon, it all depends on the user's requirements: heavy computing tasks will be served better with a C2D. However, general computing (incl. games and wo' 'av 'ye) can be done rather decently on a dual core AMD. In addition, the AMD X2s and their traditionally paired NVIDIA chipsets are well supported by Linux, whereas many a C2D board (especially the 965-based ones) may cause a few hiccups here and there.

So, mainstream computing? Office work? Games? Webbing? AMD should prove an adequate choice. CPU-intensive stuff? Perhaps an Intel-based board would be better. But then again, how often would you perform these CPU intensive tasks....

---

### Post by zekopeko on 2007-01-23
^^^

you are right. didn't think about drivers for the mobo.

---

### Post by dannyboy79 on 2007-01-24
you know it's funny, this guy asked for our feedback, we give him some then he doesn't comment back?? what's up with that?

---

### Post by jrib on 2007-01-26
> **zekopeko said:**
> 
but what is the price diffrence for Core 2 Duo 2Ghz and this AMD?

The actual price difference between an E6300 and the 3800+ is about 50 dollars.

The motherboards for core 2 duo seem to be more expensive as well.  I'm still considering the c2d though just because of all the great reviews.  But then I'm also worried about the fact that a lot of people seem to be having problems getting a c2d and motherboard to work properly on linux.

As you can tell, I'm not in a rush to build this system, so I'll take some time weighing my options.

> **dannyboy79 said:**
> you know it's funny, this guy asked for our feedback, we give him some then he doesn't comment back?? what's up with that?

I don't check the boards daily :)


Thanks for the comments everyone

---

