---
title: "new desktop - hardware recommondations"
date: 2008-07-11
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-07-11
Hi all.
Sometimes unexpected things happen. So, now I want to buy a new desktop, Linux friendly of course. I have build my own computers in the past, means I'm not exactly an total beginner with this. However, that was back in the day when GHz processors where still a cool thing. :KS
In other words, I lost track on hardware and need some advise about what to get. To get that straight, I don't even know what the big difference is between Intel and AMD processors anymore. Which is better for what task, who has better cache, are the Triple-Core AMDs worth the money, are they actually all 64Bit now? :-k

Well, I guess I need some advice here what I should look for. Calculated conservative I have about 750AU$. So, I got that money in Euro but live in Australia, means I need to transfer the money on a good day and then I might have a bit more.

OK, my general usage profile is quite some web (can be 2 Firefox each with 15-20 tabs or more each), lot of emails, web development (therefore multiple different browsers to test sites), rather light graphic design (Inkscape, Gimp), word processor, spread sheets, VoIP and IM, etc. I would like to try a little bit of video editing and sound recording but that is by no means a priority.
Basically I have many programs opened at once. Might even be that a DVD is playing in the background and I'm only listening to it. Bit strange, I know, but I don't care... ;) So, over all I'm more in need of RAM then processor speed. Also, I'm not too much into games.

Here is what I'm looking for:
[LIST]
[*]Probably a 64bit system for the sake of getting 4GB RAM.
[*]DVD-R R/W
[*]A solid video card but not too fancy, good enough for a 3D game every now and then, and Compiz would be nice (my hardware doesn't do it...)
[*]Processor? Dual-Core or is it worth getting a AMD Triple-Core? I don't think that I need a Quad-Core.
[*]Cooling can be a bit over-sized to keep the fan speed down. Case fan is most likely necessary, though. It's getting quit hot in summer.
[*]Also I'm thinking of 2 SATA HDD, make a software RAID and mirror the drives. Would that be a good idea? Is it complicated to restore such a RAID if one HDD fails?
[/LIST]

So, that is the idea so far. But I really don't know where to start with. If been looking online, in particular at [http://pricepoint.com.au/shop/]("http://pricepoint.com.au/shop/") but as I said I'm not the hardware guru. Is it possible to build such a system for about 750AU$? What hardware would you recommend for that? 

Thanks for any input.
Cheers.
:guitar:

---

### Post by Linux&amp;Gsus on 2008-07-12
no one out there who can give me some advice? :(

---

### Post by Vivaldi Gloria on 2008-07-12
Intels have been better lately. If I were you I'd buy a good gigabyte mobo like this

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128337](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128337)

or better. The only problem I might have with that board is that it has only 4 sata connections. I'd like to be able to attach more hard disks. 

This is an intel LGA 775 motherboard. LGA 775 is the current intel architechture. You can put both core 2 duo and quadcore processors on it. Every processor out there is 64bit btw. I have installed two processors on a similar gigabyte board: 1) Intel quadcore Q6600. 2) Intel Core 2 Duo E7200. Quadcores are good if the programs you use are multithreaded. E7200 is a new budget core 2 duo and i really like it. Even such a lower end core 2 duo is extremely powerful. 

Put 4GB 800mhz ddr2 kingston RAM. ddr3 rams are available but still expensive. 

I don't know much about video cards because I never needed any fancy card. Today even an onboard card like intel 3100 can run compiz! If you are not going to play 3D games then you don't need a high-end card. A card which has, say, an nvdia 8600gt processor is more than enough to satisfy a non-gamers needs.

IDE connectors are dead. By a couple of sata drives and a sata dvd writer. I never raided my disks so I cannot comment on that.

I really like a silent pc. So I'd buy a good heatsink with a 120mm fan. I have a thermalright si-120 heatsink and I'm quite happy with it. The only problem with it is that it comes with "amd legs" and you also have to buy a lga775 adapter. Stock intel heatsink & fans are noisy.

Some cases come with powersupplies, some don't. I prefer buying a empty case and add a decent powersupply with 120mm fan. I really hate smaller fans.

Have fun.

---

### Post by fragos on 2008-07-12
All processors are 64 bit now but I still run a 32 bit kernel. I judge memory requirements by looking at my swap useage with "free" in a terminal. With 1GB and swappiness set to 10 I almost never swap. Ergo, for me 1GB is plenty. I develop web sites and do a lot of graphics editing with a TV window open as well. Dual core is plenty for a desktop. When you buy disks, make sure they're 7,200 RPM and have a large cache -- 8MB OK but 16 MB is better. I prefer Western Digital. For video, stick with Nvidia -- they have the best track record for Linux support. Even the least expensive Nvidia cards will run Compiz well. To be honest, my desktop is an AMD Sempron 2800+ with 1GB, 7,200 RPM 16MB cach drive, and an old AGP Nvidia FX5200. It runs well -- anything you buy will be more powerful. My laptop is a Dell 1420n with an Intel Core DUO, 1GB and Intel X3100 video. The old desktop boots and loads programs faster. If I were to buy today, I'd go AMD X2, (2) 1GB DDR2 and an entry level PCI Express 16 Nvidia card. Note that two same spec memory carsd are about 10% faster than the same memory in one card.

---

### Post by Linux&amp;Gsus on 2008-07-13
Thanks guys, helps a lot to look where to start.
I'm still open, though, for more suggestions.

@Vivaldi Gloria
Interesting point with the Intel heatsink/fan.

@fragos
I hear you with Nvidia for graphics. I guess my trouble with not able to run Compiz is that all my video cards happen to be ATI.
Anyways, about the RAM, well my laptop has 1.5GB and I do use/need swap. As I said I can have a ton of apps running at the same time. My laptop still performs the best, though. Even if it has "only" an 1.7GHz Intel Centrino. The current desktop has an 2.5GHz Celeron with 1GB RAM and is many times rather slow. My test box is a 1.6GHz AMD Duron with 512MB RAM and a 32MB video card. Still, Hardy runs fine but of course not as good as on the laptop.

Having said that, I know that I don't need the latest Quad-Core and actually I don't want to have one. But I'm looking for something that will last me for quite some years.

Another question I have is about Java. My wife likes to play Catan online. It's a Java based game. So, what would be best for Java, are the any differences at all between AMD/Intel and 32/64 Bit OS? Or does that purely depend on the program? Because it's very sluggish but has no 3D or anything fancy really.

Also the question about the HDD remains. Is that a good idea to RAID the disks? Is it difficult to rebuild a RAID?
I guess I'll will stick to WD or Seagate disks (250GB or 320GB max). Any comments, pro or con, about that?

Cheers.
The one who's about to grab his guitar and plays some tunes. :guitar:

---

### Post by fragos on 2008-07-13
Java can be a memory hog doesn't perform as well as a program written in a language like C. Raid can be configured in different ways. At one it's redudancy and at the other focuses on performance. I haven't bothered with it. I do however backup my working data with "unison". I backup over WiFi with a working copy on my desktop and laptop. My web sites are kept on an FTP server at GoDaddy.com in my hosting account.

---

### Post by hansdown on 2008-07-13
Hi linux&gsus. I just bought my new box, and after installing 8.04 using entire disk, have been rocking on.

---

### Post by Linux&amp;Gsus on 2008-07-13
"Java...doesn't perform as well...C" While I'm fully aware of that fact, it's described very, say, kindly. It's more like you press the button to role the dice and then grab a cuppa. :D Really, it's not just a fraction of a second delay. Often, not to say most times, it takes a few seconds to do its thing. Also it freezes quite frequent.
That's why I'm asking what could be done to improve that experience.

About the RAID, well, I want to mirror the 2 disks. For one it gives me a backup against hardware failure. Not human error, I am fully aware of that. Also it increases read speed. Which isn't really anything bad, I suppose. ;)
I know that a hardware RAID would be better but since we are not talking about server grade hardware I find it a bit too risky to get hardware RAID and then maybe no replacement in case of failure. Si, I want to go with a software RAID, knowing that it's not quite performing as good but I guess good enough. At least good enough to not perform worse than without RAID but still having the convenience of the backup.

---

### Post by Linux&amp;Gsus on 2008-07-13
> **hansdown said:**
> Hi linux&gsus. I just bought my new box, and after installing 8.04 using entire disk, have been rocking on.


Hi hansdown,
while I'm glad to hear it some detail about the hardware would be nice. Well, and may I ask would that be within my price range of about 750AU$?

---

### Post by fragos on 2008-07-13
I'm only stabbing in the dark but have you tried Sun Java 6? It's in the Ubuntu repositories.

---

### Post by CatKiller on 2008-07-13
I find the [Ars Technica system guides]("http://arstechnica.com/guides/buyer/guide-200805.ars") to be quite informative. Having said that, I recently built a computer for my other half for really cheap with some bits that I had lying around and a Pentium DualCore E2180, GigaByte GA-G31MF-S2 motherboard, 2GB of DDR2 and a quiet 400W power supply. She loves it, and it runs Compiz fine with its integrated Intel graphics. That board will happily take 4GB of RAM. It came to, like, £180 for the bits that I bought.

As an aside, since you've had performance problems with Catan Online, have you tried Pioneers? My friends and I really enjoy using that to play Settlers of Catan over the local network or over t'Internet.

---

### Post by Linux&amp;Gsus on 2008-07-14
> **fragos said:**
> I'm only stabbing in the dark but have you tried Sun Java 6? It's in the Ubuntu repositories.

Yes, it's Java 6 and installed from the repos.

---

### Post by Linux&amp;Gsus on 2008-07-14
> **CatKiller said:**
> I find the [Ars Technica system guides]("http://arstechnica.com/guides/buyer/guide-200805.ars") to be quite informative. Having said that, I recently built a computer for my other half for really cheap with some bits that I had lying around and a Pentium DualCore E2180, GigaByte GA-G31MF-S2 motherboard, 2GB of DDR2 and a quiet 400W power supply. She loves it, and it runs Compiz fine with its integrated Intel graphics. That board will happily take 4GB of RAM. It came to, like, £180 for the bits that I bought.

Well, I don't have any parts laying around. Aside the broken laptops. But for sure not for desktops. Anyways, that Arstechnica article is a nice read. Thanks for that. Gives me some more ideas what to take care of.



> **CatKiller said:**
> As an aside, since you've had performance problems with Catan Online, have you tried Pioneers? My friends and I really enjoy using that to play Settlers of Catan over the local network or over t'Internet.

Well, it's not really myself having the trouble. My wife is playing that. To be honest I have no clue about that game. All I know is that she has some trouble with it. But I can mention it to her. But can't guarantee that she'll have a look at it.

Cheers.

---

### Post by CatKiller on 2008-07-14
> **Linux&Gsus said:**
> Well, I don't have any parts laying around. Aside the broken laptops. But for sure not for desktops. Anyways, that Arstechnica article is a nice read. Thanks for that. Gives me some more ideas what to take care of.

No worries. The bits that I re-used were keyboard/mouse, monitor and speakers. Everything else was onboard with the new motherboard. Nothing too expensive, really. Especially since an Internet cafe near me has recently transitioned from rather nice 21" CRTs to LCD screens, meaning that they are offloading monitors to anyone that will take them away. Perhaps there's someone that's doing something similar near you?

> Well, it's not really myself having the trouble. My wife is playing that. To be honest I have no clue about that game. All I know is that she has some trouble with it. But I can mention it to her. But can't guarantee that she'll have a look at it.

Cheers.

Sure. Good luck!

---

### Post by Linux&amp;Gsus on 2008-07-19
OK, here we go. I made a list with some components. What I don't really know yet is whether all that really fits together and if it's the best value. But maybe someone can help me out with that. As I said at the beginning I haven't followed the hardware business lately.
I added links to an online shop for further clarification on the components.

----------------------------------------------------------------------
Motherboard:
Gigabyte GA-MA74GM-S2H M/b - AMD 740G/SB700 chipset, DDR2 800, PCI-E x16
[http://www.pricepoint.com.au/shop/product_info.php?products_id=16428](http://www.pricepoint.com.au/shop/product_info.php?products_id=16428)

CPU:
AMD Phenom X3 Triple Core 8450 2.1GHz, AM2+
[http://www.pricepoint.com.au/shop/product_info.php?products_id=16841](http://www.pricepoint.com.au/shop/product_info.php?products_id=16841)

CPU Cooler:
Asus SILENT- KNIGHT II CPU Cooler Pure Copper - Made for Quad-Core CPUs, Support Socket 775 and AMD/AM2
[http://www.pricepoint.com.au/shop/product_info.php?products_id=17223](http://www.pricepoint.com.au/shop/product_info.php?products_id=17223)

RAM (2x):
PC-4200-9136 (533-1142 MHz) - 2GB PC-6400 (800MHz) 240-pin DDR2 RAM OEM
[http://www.pricepoint.com.au/shop/product_info.php?products_id=17174](http://www.pricepoint.com.au/shop/product_info.php?products_id=17174)

Video Card:
Galaxy GF8500GT PCI-E 512MB DDR2 128-bit, Overclocked, 500MHz/700MHz
[http://www.pricepoint.com.au/shop/product_info.php?products_id=13895](http://www.pricepoint.com.au/shop/product_info.php?products_id=13895)

Optical Drive:
Samsung SH-S223F
[http://www.pricepoint.com.au/shop/product_info.php?products_id=17480](http://www.pricepoint.com.au/shop/product_info.php?products_id=17480)

HDD:
a) Samsung 320GB HD322HJ HDD - SATA II 7200rpm, 16MB
[http://www.pricepoint.com.au/shop/product_info.php?products_id=16973](http://www.pricepoint.com.au/shop/product_info.php?products_id=16973)

b) Hitachi 320GB DeskStar T7K500 - 3.5 SATA 3.0Gb/s HDD, 16Mb
[http://www.pricepoint.com.au/shop/product_info.php?products_id=16955](http://www.pricepoint.com.au/shop/product_info.php?products_id=16955)

Case/PSU:
Antec NSK4480B Solution Series ATX MiniTower - Black, EarthWatts 380W PSU, Drive Bays: 3x5.25 & 2x3.5 External, 3x3.5 Internal, 2 x USB
[http://www.pricepoint.com.au/shop/product_info.php?products_id=13610](http://www.pricepoint.com.au/shop/product_info.php?products_id=13610)
----------------------------------------------------------------------


I must say that the more I think about it the more I like the idea of the AMD Triple Core. The apps I use really don't need some turbo-charged 3GHz CPUs. So, I figured a more but slower cores might be actually better. The Quad Cores, though, might be really way over the top of my needs and therefore not worth the extra 40$, for me anyways.

About the RAM, is it actually better to have 2x2GB or 4x1GB. Does it make a difference at all?

The HDDs, well 250GB would be more than I have now but I figured the extra cache with those 320GB drives might be beneficial. Also, if I don't get 2 identical drives they're less likely to break at the same time. Which would defeat the purpose of the RAID that I envisioned.

Is the 380W PSU big enough? With the CPU already eating ~100W there's ~280W left. I have no clue how much the GPU is sucking up. But it should be big enough, right?

Thanks for any advise.
Cheers.

---

### Post by Linux&amp;Gsus on 2008-07-20
Send to top.
Commonly known as "bump" :)

---

### Post by CatKiller on 2008-07-20
I don't really know much about multi-core processor usage, I'm afraid. And with regards to the memory, it used to be the case that if you had more slots populated, you could have more simultaneous read/write operations. I don't know if that's still true of modern memory controllers.

Quality of the power supply is generally more important than rated capacity; some lower-quality manufacturers would list a much higher capacity than the PSU could actually provide in constant usage. 400W used to be sufficient, and I believe that components are more efficient these days than, say, the Athlon T-Bird that I used to have. Another consideration for the PSU is that some high-performance graphics cards need an extra power source than what they draw from the PCI bus. It's probably worth checking if the graphics card you've selected needs this, and if the PSU can provide it.

Sorry, I appear to be offering you more questions than answers.

---

### Post by Linux&amp;Gsus on 2008-07-20
Hi CatKiller,
more questions might be true. But those are good questions. Just the ones I need, specially in regards to the PSU and video card. Although, I don't think that those kinda cards considered "high-performance". But I'll better check it out anyways.
With the quality of PSU I agree with you. I, however, don't think that a 380W PSU is over-advertised. It's not like a ridiculous cheap 1000W thing. Still the graphics card thing is something I'll check.

Anymore suggestions? BTW, is a Samsung and Hitachi HDD a good choice or are the known to give trouble?

Thanks a lot.

---

### Post by songshu on 2008-07-20
i never used them but i heard that the samsung spinpoint F1 is a killer (positively speaking)

further then that i can say i had a lot of luck with several gigabyte mobo's, they might even be my linux board of choice. always had small issues with asus personaly.

i would say invest heavily in a good PSU and cheap DDR2 RAM, DDR3 has a very slight advantage and is expensive.

any late P4 or equivalent AMD will serve you well and these are cheap nowadays.

---

### Post by fragos on 2008-07-20
Antec has a good reputation. This is a link to the Antec page for this supply:

[http://www.antec.com/us/productDetails.php?ProdID=27380](http://www.antec.com/us/productDetails.php?ProdID=27380)

This is a forum link where this specific suppply was tested:

[http://www.ocforums.com/showthread.php?t=512807](http://www.ocforums.com/showthread.php?t=512807)

---

### Post by Linux&amp;Gsus on 2008-07-21
Good info, guys, thanks. Also nice links, fragos.
@CatKiller
From the link to Antec that fragos posted. Is that the extra power source for graphics cards you're talking about?
> PCI-E connector: one for 380W and 430W, two for 500W

What I find interesting, though, is that the PSU has 4 SATA connectors. Are there splitter available to split power for 2 SATA drives? Since you can install up to 6 SATA drives I find that a bit strange.

The following (from the Antec site as well) is power for RAM, Case fans, etc, right?
> Dual 12V outputs: 12V2 for Motherboard and peripherals; 12V1 for processor




Cheers & Thanks.
You guys rock.

---

### Post by CatKiller on 2008-07-21
> **Linux&Gsus said:**
> @CatKiller
From the link to Antec that fragos posted. Is that the extra power source for graphics cards you're talking about?

Yep, that's the one.

> The following (from the Antec site as well) is power for RAM, Case fans, etc, right?

More-or-less. The RAM & case fans are powered by the motherboard. Some chipsets require another 12V rail for the processor, and often this connects to the motherboard near the processor.

---

### Post by Linux&amp;Gsus on 2008-07-22
Right, the power itself comes via the motherboard. Was a bit confusing how I wrote it, sorry bout that.
What I really meant was an additional power point to stabilize the power for RAM, CPU, whatever else. I remember after I built a computer the last time there was something like this for Intel based computers to stabilize the power for the RAM.
Well, that's how long I haven't done anything like that anymore... :)

Anyways, thanks for all infos guys. I'm currently checking some more prices before I'll really finalize the components.

Cheers. :KS

---

