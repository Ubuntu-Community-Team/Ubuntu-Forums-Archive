---
title: "Should I build or buy a new desktop PC for Linux?"
date: 2015-03-07
forum: Hardware
---

### Post by swhit3 on 2015-03-07
Greetings Ubuntu Community,

My Asus u56e laptop has bit the dust sadly and I'm looking to build or purchase a new desktop to run Linux. I'm wondering what people think nowadays is good for Linux support. AMD or Intel for CPU? Is it much cheaper to build my own desktop or should I just spend the money on a System76 or ZaReason tower? My budget is no more than 1,000 USD, and I will need to factor in a monitor display into that cost as well. Things I'm looking for are at least 500GB HDD, not sure about processors, graphics card could be integrated, but if its better to settle up to an nvidia or amd let me know, and gotta have wireless ready. Any thoughts? Thanks for any help in advance!

---

### Post by Mark Phelps on 2015-03-07
I've used AMD processor-based systems on Linux distros for years and haven't encountered any problems.  Current desktop is an AMD processor and works just as well on Linux as it does in Windows.

As to "buy or build", I spent years building rigs for my extended family, finding it cheaper to buy and assemble the parts than to purchase prebuilt systems.  But a few years ago that all changed when I could buy any number of mid-range systems for under $500.

Nowadays, unless you need specific components, or some kind of specialized system, it's generally cheaper to buy something ready made than to pay retail cost for the parts and assemble it yourself.

But, since I haven't done this recently, others may have more current experience and advise you otherwise.

---

### Post by TheFu on 2015-03-07
After being burned with a "deal" from a PC maker using proprietary components that could only be replaced by parts from that vendor, I build my own.

Building is easier now than ever before.  Everything is keyed - it only fits 1 way. Most things will come with a manual and there are thousands of youtube videos with people building systems.

The last 8 yrs, I've never spent over $450 for the parts. It really depends on what you need the PC to accomplish.  For a fast-enough desktop, there are $100 MB+CPU+GPU combos happening here that really amaze me. Sadly, I purchased the same stuff 2 weeks earlier through amazon - when that was $126 and I'm building that system today.  Of course, I have spare parts from old builds - like a case, PSU, HDDs and RAM.

You mention laptops - those are completely different.  It doesn't make any sense to build a laptop.

Using a web app like **pc part picker** will help you put together a system that is compatible.  Steps:
* pick a CPU
* determine if the GPU that comes with the CPU is enough or not.
* pick a MB that the CPU fits.  Lots of how-to guides for this. Make certain the MB has any slots, USB3, video out, audio, networking you want. If you need an extra GPU - ignore the MB video. Might be a good idea to ignore MB networking too, since those chips aren't as compatible as Intel PRO/1000 (only $25, but eat a slot)
* Lots of CPUs come with stock coolers - my last purchase did (Intel G3258) and with that cooler it can be over-clocked 20%.
* Case - 
* PSU - if you are a high end gamer and need $300 GPUs, you'll need a PSU that can power them. Otherwise, a 430W Bronze will be fine. I always get Bronze or higher and have had good luck with Seasonic and Corsair - there are online articles from large scale PC makers which talk about which PSUs work best/longest.
* HDD - 500G is $50 or less. Doesn't matter much, though I've been burned by Seagate failures more than any other maker. There are reliability reports which say seagate is by far the least reliable maker - at least for desktop drives. Don't know anything about their SAS.
* RAM ... It all works and I haven't seen any that didn't have a lifetime warranty.  G.Skill has been a good brand for me, but I've used Kinsington, Crucial, and a few others. The only memory that gave any issues was Balistics ... it only worked in 1 system here and I wasn't able to ever find any matching RAM.  Probably user error.  RAM will tell the MB what speed and voltage to use now.

Of course all this is my experience and extremely small numbers of parts. Definitely NOT a statistical sample.

If you need everything buying a complete PC can make sense - just be careful to know which components can be swapped out later with normal parts from your local PC shop, not only that vendor.  

I wouldn't spend over $450 for a built system.  I nice Core i5 is a pretty powerful system.  Shuttle was selling Core i7 boxes for $450 a few years ago - pick one up for Mom with a high-end CAD GPU. That's different than a gaming GPU.

Anyway - lots of smart folks here. Hope you get lots of input.

---

### Post by philo565 on 2015-03-08
I have done nothing but build my own machines. You should easily be able to come in under budget. Lately I've been using those inexpensive all-in-one motherboards that have the non-replacable CPU. Lets' face it, how often does one replace a CPU? I've never seen one fail. DDR-3 is cheap ... 8 gigs of ram will cost very little. Also: I would not bother getting less than a 2 gig HD unless you are going with SSD.

I have plenty of spare cases here and find those mini-ITX boards will fit in an ATX formfactor

---

### Post by weatherman2 on 2015-03-08
I've built numerous systems over the years.  Unless you get a great deal (I have an eye for them), you probably won't save much money if any building your own system, though. What you get is the ability to choose your own components and also probably a BIOS or firmware with many more options than a stock manufacturer's board would have.

But $1000 USD will buy you a really nice computer.  You can surely build a decent one for half of that, unless you really need big expensive monitor(s).

SSDs are now so cheap that I'd almost certainly get an SSD just for the operating system and a hard drive for the data, if you really have that much.

I like Intel CPUs myself - just a preference.

I wouldn't get a separate graphics card unless you plan to use the system for gaming.  A modern (4th Gen Haswell or newer) i5 CPU would be really fast.  An i7 might be overkill depending on your intended use of the computer.

You also don't need a big power supply.  400 watts is plenty (probably more than you need) for a modern system unless - again - you would be gaming with a separate graphics card.  Get an 80+ efficient power supply.

You can get a USB wireless card easily.  Or get an internal card that plugs into a mini-PCI "laptop" slot (also need antennas).  Some desktop motherboards have mini-PCI slots, others have standard PCI-E slots into which you can plug wireless cards or adapters to use mini-PCI wireless cards.  Lately I prefer to use a separate router for wireless, setup as a wireless ethernet bridge, so that the desktop itself doesn't have wireless but with the ethernet bridge you connect to your wireless network without a cable.  One advantage of the ethernet bridge: no separate wireless driver to hassle with (often a pesky issue in Linux).  Another advantage is that you can use Wake-On-Lan (WOL) to wake up your desktop remotely, assuming the ethernet bridge/router is always connected and on.

Desktop "tower" computers are fading away.  They are already much bigger than needed anymore, probably because people are used to that form factor.  I'm going with smaller and smaller whenever I can nowadays.  If you aren't gaming, chances are you won't be adding many cards to the board anyway.

---

### Post by warren3 on 2015-03-08
Get a Gigabyte Brix.  i3 or i5 should do.  I'm using an i3 with 120gb msata SSD,500gb HD, 8GB RAM, all in a tiny box.  Runs Ubuntu really well and uses hardly any power - it will probably pay for itself in saved electricity in a year or two.

---

### Post by SeijiSensei on 2015-03-09
For a basic desktop workstation, I just buy OEM machines.  My latest purchase was this ASUS: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883220835](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220835).  It was on sale for $449 ($100 off current price) which was as good a deal as I could find for a machine with an i5, a terabyte hard drive, 8 GB of memory, and Windows 7.  The Intel graphics chip works fine for video sources.  If I wanted to play games I'd probably invest in a midrange video card like [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500348).  

It doesn't have built-in wireless but you can just use a USB or PCI adapter.  I'm using this TP-Link device: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045) in the ASUS.  For my daughter's computer, we bought this PCI adapter: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833166073](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166073).

---

### Post by mastablasta on 2015-03-09
with that money and for your needs something Intel might be the way to go. If you want to spend less AMD has some good APU's and a good price. The chips there are still better than Intel's I believe. They do draw a bit more power though. 

oh and at least here there is almost no difference in price between 500 GB disk and a 1 TB disk.

---

### Post by pqwoerituytrueiwoq on 2015-03-09
yea the on sale price difference is $9
500GB on sale is 41 (wd blue)
1tb is 49.99 (wd blue)
1tb toshiba is 45 onsale
iv only had 2 HDDs ever die, both WD, but were subject to unusual situations
one had a molex plug connected upsside down, so the +5 and +12 were reversed which fried the circuit board (don't use molded made in china plugs in the dark were you can't see what way the plug is keyed)
one was subject to a harsh environment and was very old

for a basic budget system i would still make my own and use a small SSD, it is rare that people really need that much space on a basic use system and all the OEM budget systems use a mechanical HDD which is slow

for a linux system i would suggest a Pentium Intel (1150 socket) over a APU, for a basic use system, just to avoid issues with fglrx
example [B][COLOR=#ff0000]
[/COLOR][/B]with your budget you can do much better than this, easily make a decent gaming class system
if you are going for a gaming system id suggest either a FX-6350/FX-6300, Pentium G3258 (if you are going to OC), or a i5 for the CPU and a GPU costing around $120+ (you will probably want to go with nvida for linux gaming, cause of driver performance)
[TABLE]
[TR]
[TH="colspan: 2"]Item[/TH]
[TH]Quantity[/TH]
[TH]Price[/TH]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/27-151-266-02.jpg[/IMG][/TD]
[TD][SAMSUNG DVD Burner SATA Model SH-224DB/BEBE - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827151266")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$19.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16827151266%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/11-352-032-02.jpg[/IMG][/TD]
[TD][Fractal Design Core 1000 FD-CA-CORE-1000-USB3-BL Black Steel MicroATX Mid Tower Computer Case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811352032")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$36.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16811352032%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/17-371-033-02.jpg[/IMG][/TD]
[TD][Antec EarthWatts Green EA-380D Green 380W Continuous power ATX12V v2.3 / EPS12V 80 PLUS BRONZE Certified Active PFC Power ...]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371033")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$44.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16817371033%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/20-146-746-05.jpg[/IMG][/TD]
[TD][Mushkin Enhanced 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1066 (PC3 8500) Dual Channel Kit Desktop Memory Model 996573]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820146746")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$36.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16820146746%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/13-157-483-02.jpg[/IMG][/TD]
[TD][ASRock H81M-DGS R2.0 LGA 1150 Intel H81 SATA 6Gb/s USB 3.0 Micro ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157483")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$45.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16813157483%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/19-117-449-01.jpg[/IMG][/TD]
[TD][Intel Pentium G3250 Haswell Dual-Core 3.2GHz LGA 1150 53W Desktop ProcessorIntel HD Graphics BX80646G3250]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117449")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$64.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16819117449%7C1")[/TD]
[/TR]
[TR]
[TD][IMG]http://images10.newegg.com/ProductImageCompressAll/20-226-678-05.jpg[/IMG][/TD]
[TD][Mushkin Enhanced ECO2 MKNSSDEC120GB MKNSSDEC120GB 2.5" 120GB SATA III MLC External Solid State Drive (SSD)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820226678")[/TD]
[TD="align: center"]1[/TD]
[TD="align: right"]$54.99
[Add to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16820226678%7C1")[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Subtotal:[/TD]
[TD="align: right"]$304.93[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Shipping + Tax:[/TD]
[TD="align: right"]$13.75[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Promo Code: EMCAPAP23[/TD]
[TD="align: right"]-$6.00[/TD]
[/TR]
[TR]
[TD="colspan: 3"]Grand Total:[/TD]
[TD="align: right"]$312.68[/TD]
[/TR]
[TR]
[TD="colspan: 2"]There is 1 Mail-in Rebate: [$15.00]("http://images10.newegg.com/uploadfilesfornewegg/rebate/SH/ANTEC17-371-033Mar5Mar1115ff31.pdf")[/TD]
[TD="colspan: 2, align: right"][Add all to cart]("http://secure.newegg.com/Shopping/AddToCart.aspx?Submit=ADD&ItemList=N82E16827151266%7C1,N82E16811352032%7C1,N82E16817371033%7C1,N82E16820146746%7C1,N82E16813157483%7C1,N82E16819117449%7C1,N82E16820226678%7C1")[/TD]
[/TR]
[/TABLE]

**[COLOR=#ff0000][SIZE=4]THIS IS A BASIC GENERAL USE SYSTEM (internet, netflix, email, etc)[/SIZE][/COLOR]**

---

### Post by TheFu on 2015-03-09
The G3258 is $49 at microcenter now - better CPU than the G3250.  Picked one up on amazon a few weeks ago for $63. They are very close, but the 3258 IS a little better.

---

