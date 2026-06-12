---
title: "Building an Ubuntu gaming PC"
date: 2014-07-20
forum: Hardware
---

### Post by Tetrapack on 2014-07-20
Greetings comrades!
I'm planing to build myself a gaming computer running Ubuntu (or possibly SteamOS). This is the first time that I'm building a PC so I'm rather paranoid to get something wrong. I will be using it mainly to play games that support Linux natively but also some Windows games via Wine. I don't think I'll be playing many "next-gen-titles" on this computer but I'd like it to last a few years before upgrading. After weeks of research and tea consumption I've chosen the following Hardware:

**Processor -** [AMD FX-6300]("http://www.amd.com/en-us/products/processors/desktop/fx")
**Video card -** [Gigabyte GeForce GTX 760 2GB WINDFORCE]("http://www.gigabyte.com/products/product-page.aspx?pid=4663#sp")
**Motherboard -** [Gigabyte GA-970A-DS3P]("http://www.gigabyte.com/products/product-page.aspx?pid=4591#ov")
**Memory -** [Kingston HyperX Grey 8GB]("http://www.kingston.com/en/hyperx/memory/pnp")
**Storage(SSD) -** [Crucial MX100 256GB]("http://www.crucial.com/ProductDisplay?storeId=10151&urlLangId=-1&productId=12929&urlRequestType=Base&langId=-1&catalogId=10151&cm_mmc=affiliation-_-null-_-null-_-null")
**Optical drive -** [Is for babies!]("http://cdn.memegenerator.net/instances/500x/44878456.jpg")
**Power supply -** [XFX 550W]("http://xfxforce.com/en-us/products/ts-series-full-wired/ts-series-550w-psu-p1-550s-xxb9")
**Case -** [Bitfenix Comrade!]("http://www.bitfenix.com/global/en/products/chassis/comrade")
**Monitor -** [BenQ GL2450]("http://www.benq.com/product/monitor/gl2450/")

Before I start ordering parts there are a few questions that I'd like to ask:

**1)** I've read many times, that Nvidia has much better Linux drivers than AMD does this still apply? (no matter if open source or proprietary drivers)

**2)** Are any of those parts inherently incompatible with Linux (especially the motherboard) ?

**3)** Is it worth it to buy 1866MHz RAM instead of the 1600MHz I have chosen or is the performance increase negligible?

**4)** Am I about to create a bottleneck somewhere?

**5)** I am currently using a rather old Laptop with a GT 240M video card (stop laughing!) and having some really annoying problems with the proprietary video drivers (Version 331) causing my screen to go black randomly and forcing me to hard reset the computer. Does anyone have similar problems with the GTX 760?

**6)** Most PSU calculators estimate the Energy consumption of my soon-to-be-machine at about 350W. However, according to the [specifications]("http://www.gigabyte.com/products/product-page.aspx?pid=4663#sp"), my video card requires at least a 500W power supply. What does that mean? Is the 550W PSU really sufficient to power the whole system under load?

**7)** Am I about to make some other horrible mistake that I can't even conceive of??

**BONUS QUESTION)** Will it run Skyrim through Wine at more than 4 seconds per frame?



**Edit (22.Jul.2014):** Changed Storage from [Kingston SSDNow V300 240GB]("http://ssds.findthebest.com/l/133/Kingston-SSDNow-V300-240GB-SV300S37A-240G") to [Crucial MX100 256GB]("http://www.crucial.com/ProductDisplay?storeId=10151&urlLangId=-1&productId=12929&urlRequestType=Base&langId=-1&catalogId=10151&cm_mmc=affiliation-_-null-_-null-_-null")

---

### Post by Yellow Pasque on 2014-07-20
You may want to look at the Crucial MX100 SSD. TechReport.com thinks highly of it, and I think highly of their reviews ( [http://techreport.com/review/26747/tr-july-2014-system-guide/6](http://techreport.com/review/26747/tr-july-2014-system-guide/6) )

> Are any of those parts inherently incompatible with Linux (especially the motherboard)
You may have to perform some workarounds for that board: [http://ubuntuforums.org/showthread.php?t=2111223&p=12851568#post12851568](http://ubuntuforums.org/showthread.php?t=2111223&p=12851568#post12851568)

> Is it worth it to buy 1866MHz RAM instead of the 1600MHz I have chosen or is the performance increase negligible?
Not worth it, unless you're OC'ing a CPU with a locked multiplier.

> Am I about to create a bottleneck somewhere?
Not a glaring one, but the CPU could be faster. Unless you're doing a lot of video encoding or running multiple VM's, a Pentium Anniversary (G3258) chip would be better for gaming (and better on the wallet).

---

### Post by WinEunuchs2Unix on 2014-07-20
Would Ubuntu be the right flavor of Linux for gaming?  I recall one distro whose claim to fame was efficiency such that it ran with 64MB of RAM and didn't even include Xorg as a default.

---

### Post by Yellow Pasque on 2014-07-21
> Would Ubuntu be the right flavor of Linux for gaming?

I think you should start a new thread if you want to discuss that.

---

### Post by mooreted on 2014-07-21
If you check Phoronix, most Linux distros have the same performance with Ubuntu coming out slightly ahead on some tests. They all tend to use the same GCC compilers and video card drivers.

---

### Post by WinEunuchs2Unix on 2014-07-21
> **mooreted said:**
> If you check Phoronix, most Linux distros have the same performance with Ubuntu coming out slightly ahead on some tests. They all tend to use the same GCC compilers and video card drivers.

I already had more than enough speed with Ubuntu.  Nice to know I actually have more than more than enough :D

I don't play games BTW.

---

### Post by Tetrapack on 2014-07-22
Thanks for the help so far.
I am convinced by the MX100 SSD but for the CPU I would rather stay with the FX-6300 because 2 cores don't really seem future proof when multi-threading is becoming more and more important. I have also noticed that my RAM takes 1.65V but the motherboard only provides 1.5V. Is that a problem?

I'm still particularly curious about that video card requiring a 500W PSU thing.

---

### Post by Yellow Pasque on 2014-07-22
The RAM looks like it works fine on stock settings at 1.5V (1.65V is probably for the automatic PnP/OC'ing feature on Intel chipsets).

If you're unsure about the RAM, get something on the mobo's QVL: [http://download.gigabyte.us/FileList/Memory/mb_memory_ga-970a-ds3p.pdf](http://download.gigabyte.us/FileList/Memory/mb_memory_ga-970a-ds3p.pdf)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820233144](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233144)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820233147](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233147)
EDIT: IF you don't like tall RAM heatsinks, here's an option: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820233186](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233186)

> I'm still particularly curious about that video card requiring a 500W PSU thing. 
Nvidia and other manufacturers often inflate their PSU requirements because they have no idea what else is in the system (and PSU manufacturers have been known to play games with their Wattage numbers anyway). It also gives their tech support departments a great excuse to filter people out.

---

### Post by gordintoronto on 2014-07-22
I like having a fast computer, but what I stare at for many hours every day is my monitor. Go for an IPS monitor. HP has a nice one, the 23Xi. I'm actually using a Dell Ultrasharp, which cost a bit more, but I'm very happy with it.

---

