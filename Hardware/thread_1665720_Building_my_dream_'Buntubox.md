---
title: "Building my dream 'Buntubox"
date: 2011-01-12
forum: Hardware
---

### Post by tehowe on 2011-01-12
This should last me for a while...

AMD 1090T hexcore 3.2 Ghz
8GB (1333 DDR3 - doubt I'll notice lack of 2000)
Radeon 5850 (driver avail on ATI site)
1TB 7200 rpm for OS/Apps
2TB 5900 rpm for data ($100 bucks cheaper than 7200)
Antec 902 box (room for 3,6,or 9 front panels), 600W supply
- Front panel to include media reader, two DVD multis, and my old SB Audigy (for now)

I'll pick up one 22" Asus LCD for the time being, with option to go to 2 or 3.

Now, I probably should have posted this before putting down the deposit, but, does anyone see any HW conflicts between this setup and Lucid? I intend to run 10.04LTS Studio, but can install Meerkat Studio if there's any HW benefits to be realized there.

I thought about NVIDIA, but 3D on Ubuntu looks like it's a long ways off so going with the Eyefinity on the Radeon GPU setup seemed like a better option.

The idea is to do full-on video and audio production natively under Ubuntu. I had to drop into Windows on my old Notebook to get the job done since that OS played nicer with the low-fi Intel chipset in Vegas with DX11.

I'm stoked, picking it up on Saturday!

What would YOU do to change this setup or build your dream Ubuntu desktop, leaving aside insanely expensive options like Intel i7 quads, etc?

---

### Post by 0004tom on 2011-01-12
I don't know anything else about the hardware apart from the ATi graphics. For the same price your getting the 5850 you can pick up the new 6xxx series gpu. the 68xx pack roughly the same punch as the 58xx series cards but cost alot less, where as the 69xx sit around the same price range with more punch then the 68xx. 

Altho the 6xxx series are not supported yet in linux, they use the same driver as the 5xxx series. I'm running a VTX3D 6850 on the ATi 10.12 driver under arch linux. If you look few my post history, you'll find some information that you might be interested in abut eyefinity and certain aspects of it under ubuntu/linux.

---

### Post by cascade9 on 2011-01-13
Different case, at least DDR3 1600/1866, drop the ATI 5850 for an nvidia card, single DVD drive only, drop creative for a decent sound card, possible a SSD if I had the money.

---

### Post by tehowe on 2011-01-13
> **0004tom said:**
> 
Altho the 6xxx series are not supported yet in linux, they use the same driver as the 5xxx series. I'm running a VTX3D 6850 on the ATi 10.12 driver under arch linux. If you look few my post history, you'll find some information that you might be interested in abut eyefinity and certain aspects of it under ubuntu/linux.

>  they use the same driver as the 5xxx series

Huh, who knew? It would be nice if ATI/AMD would deign to mention it. I'll call the computer shop and see if they've driven out to their supplier to get the 5850 yet and make the substitution if I can, thanks for the tip. In this case the difference is only 15 bucks but it would be nice to be that tiny bit more future-proofed. And yeah, I've done a fair bit of searching around on here for research and saw a number of your threads come up :D

---

### Post by runeh76 on 2011-01-13
Take Nvidia to graphic!

---

### Post by tehowe on 2011-01-13
> **cascade9 said:**
> Different case, at least DDR3 1600/1866, drop the ATI 5850 for an nvidia card, single DVD drive only, drop creative for a decent sound card, possible a SSD if I had the money.

I'll probably pick up a Delta 1010 soundcard used later on when I have the money to do some more upgrading. The Audigy's just something I've got lying around once I stripped out my dead P4.

The mobo only supports 1333 RAM, unless you overclock it that is, at which point it takes 2000 - maybe in a few months I'll trade up if the price is right.

---

### Post by cchhrriiss121212 on 2011-01-13
I'd agree with what cascade said. If you want to do audio editing you should consider:
1. A dedicated sound card. Check [here]("http://www.alsa-project.org/main/index.php/Matrix:Main") for supported devices. I can recommend one if you explain what your needs are.
2. You should have 7200rpm for storing raw audio data, 5400rpm can be a bottleneck if you are trying to do multitrack recording.

---

### Post by tehowe on 2011-01-13
> **runeh76 said:**
> Take Nvidia to graphic!

But why? I heard it's basically a myth now that one's better supported than the other.

---

### Post by alaukikyo on 2011-01-13
> **cascade9 said:**
> drop the ATI 5850 for an nvidia card, 

ati card support in gnu/linux USED to be bad it isn't bad anymore.

---

### Post by cascade9 on 2011-01-13
> **tehowe said:**
> The mobo only supports 1333 RAM, unless you overclock it that is, at which point it takes 2000 - maybe in a few months I'll trade up if the price is right.
 
 2000? *blinks* I cant think of any AMD AM3 motherboard that does DDR3 2000..1800 and 2133 are more typical. What motherboard are you thinking of using? 
 
 BTW, even if you cant use faster RAM than 1333 without 'overclocking' (and BTW, thats just overclocking the RAM, not the whole system) faster RAM can run at lower speeds with lower latency, so its still better to have faster RAM. 
 
 Just make sure you dont get 'faster' RAM thats got slower timings. 

> **tehowe said:**
> But why? I heard it's basically a myth now that one's better supported than the other.

LOL, nope. AMD/ATI 6XXX STILL has no offical support, nvidia doesnt drag that much. Also, AMD/ATI XvBA is buggy, nVidia VDPAU works well. 

That is before you even talk about the actual drivers and possible problems. 

AMD/ATI does have better open source drivers though. 

> **cchhrriiss121212 said:**
> I'd agree with what cascade said. If you want to do audio editing you should consider:
1. A dedicated sound card. Check [here]("http://www.alsa-project.org/main/index.php/Matrix:Main") for supported devices. I can recommend one if you explain what your needs are.
2. You should have 7200rpm for storing raw audio data, 5400rpm can be a bottleneck if you are trying to do multitrack recording.

Surely with modern 5400s they have enough bandwidth for raw audio? My 5400 RPM (actually 5000 RPM IIRC) WD Green power drive is faster everywhere than the older SATA 7200 I was running before.

---

### Post by cchhrriiss121212 on 2011-01-13
> Surely with modern 5400s they have enough bandwidth for raw audio? My  5400 RPM (actually 5000 RPM IIRC) WD Green power drive is faster  everywhere than the older SATA 7200 I was running before.
Maybe they do, but if I were building a "dream box" for audio I would go for a 7200. 
It will depend on how many tracks you are using and how many files you have loaded at one time as well as latency settings, file size etc. I don't have any recent tests but raw audio processing is a little different than generally tested read/write times.

---

### Post by cascade9 on 2011-01-13
> **cchhrriiss121212 said:**
> Maybe they do, but if I were building a "dream box" for audio I would go for a 7200. 
It will depend on how many tracks you are using and how many files you have loaded at one time as well as latency settings, file size etc. I don't have any recent tests but raw audio processing is a little different than generally tested read/write times.

If I were building a 'dream box' it would have a SSD, a 7200 (WD caviar black, minimum 1TB) and a 'slow' drive for data storage (probably 2TB, mainly because I'd prefer to avoid host bus adapters needed for 3TB. 

AFAIK, you are right, raw audio porcessing is a little different to what is generally tested. It should still scale, but hey, I dont do audio work so you probably know more than me there. ;)

---

### Post by tehowe on 2011-01-13
> **cascade9 said:**
> 2000? *blinks* I cant think of any AMD AM3 motherboard that does DDR3 2000..1800 and 2133 are more typical. What motherboard are you thinking of using? 
 

ASUS M4A88TD-V EVO/USB3 [http://www.motherboards.org/reviews/motherboards/2067_2.html](http://www.motherboards.org/reviews/motherboards/2067_2.html)

(I figured I didn't need a Crosshair board.)

 > **cascade9 said:**
> AMD/ATI 6XXX STILL has no offical support, nvidia doesnt drag  that much. Also, AMD/ATI XvBA is buggy, nVidia VDPAU works well. That is before you even talk about the actual drivers and possible problems. AMD/ATI does have better open source drivers though.

Oh... dammit. I'm guessing ATI's Catalyst is a better performing option than the open source driver though, for Compiz and shading and whatnot. So far.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

On a slightly different topic. how transparent would this rig be for running Win7 in VirtualBox? Eg; would gaming on Win7 suffer terribly in a virtualized environment - my possibly deluded impression is that this machine should smoke at virtualization. I could install a dual boot, but if that's not necessary I'd prefer to keep things, erm, Canonical.

---

### Post by cascade9 on 2011-01-13
> **tehowe said:**
> ASUS M4A88TD-V EVO/USB3 [http://www.motherboards.org/reviews/motherboards/2067_2.html](http://www.motherboards.org/reviews/motherboards/2067_2.html)

(I figured I didn't need a Crosshair board.)


Heh, I hadnt noticed that it has DDR3 2000 support. 

You would be much better of with a 870/SB850 chipset motherbaord. I know, you dont 'need' crossfire but you also dont 'need' onboard video. The 870/890FX boards are better than the 880 boards, and if you are getting a video card, go for a 870/890FX. (the only excpetion to this is if you want a microATX motherboard). 

BTW, IMO the gigabyte boards are much nicer than the asus boards at the moment. ;)

---

### Post by cchhrriiss121212 on 2011-01-13
> **tehowe said:**
> 
On a slightly different topic. how transparent would this rig be for running Win7 in VirtualBox? Eg; would gaming on Win7 suffer terribly in a virtualized environment - my possibly deluded impression is that this machine should smoke at virtualization. I could install a dual boot, but if that's not necessary I'd prefer to keep things, erm, Canonical.
Gaming in a virtual environment is not worth trying, see here:
[http://ubuntuforums.org/showthread.php?t=1410326](http://ubuntuforums.org/showthread.php?t=1410326)
If you can't dual boot the next best option is WINE.

---

### Post by tehowe on 2011-01-13
> **cascade9 said:**
> Heh, I hadnt noticed that it has DDR3 2000 support. 

You would be much better of with a 870/SB850 chipset motherbaord. I know, you dont 'need' crossfire but you also dont 'need' onboard video. The 870/890FX boards are better than the 880 boards, and if you are getting a video card, go for a 870/890FX. (the only excpetion to this is if you want a microATX motherboard). 

BTW, IMO the gigabyte boards are much nicer than the asus boards at the moment. ;)

But, I'd be giving up HYBR1D CROSSFIR3! Lol. 

The nice thing about the 870 boards, I see, is the 1600 RAM support.

It seems you have to be selective to get 2000Mhz working with the Phenom II, so, in case anyone comes across this thread the following article may some help...

[http://www.xbitlabs.com/articles/memory/display/phenom-ii-x6-ddr3-2000.html](http://www.xbitlabs.com/articles/memory/display/phenom-ii-x6-ddr3-2000.html)

> you have to overclock your computer to be able to set that memory  frequency. With our testbed, we had to raise the base clock frequency  from 200 to 250 MHz in order to use our system memory as DDR3-2000. Of  course, this affects the rest of the frequencies as well, including the  clock rates of the CPU, CPU-integrated North Bridge and HyperTransport  bus. So, after changing the base clock rate, you may want to check out  and adjust the rest of the frequencies and multipliers. We will use a Phenom II X6 1090T for today’s tests. Its clock rate  increases from its default 3.2 GHz to 4.0 GHz as we raise the base clock  rate from 200 to 250 MHz. This overclocking suits us just fine as we  know our CPU to be able to work at such settings without any problems.

For myself, I guess I'm cuttnig a few corners on my 'dream' machine. When it comes to RAM, though, after reading through the real-world tests, I'd advise people to just go with the 1333 and "save your money"

[http://www.xbitlabs.com/articles/memory/display/phenom-ii-x6-ddr3-2000_5.html](http://www.xbitlabs.com/articles/memory/display/phenom-ii-x6-ddr3-2000_5.html)

> Gamers who use AMD platforms may achieve a 1.5% increase in performance  if they take the trouble of finding special memory capable of working  with Phenom II X6 processors at 2000 MHz. The performance benefits look  negligible if you compare platforms with similar memory frequencies but  you shouldn’t dismiss the influence of memory on performance altogether.  For example, the difference between DDR3-2000 and DDR3-1333 with the  same timings is as high as 5%.

eg;

[IMG]http://www.xbitlabs.com/images/memory/phenom-ii-x6-ddr3-2000/re5.png[/IMG]

---

### Post by 0004tom on 2011-01-13
> **tehowe said:**
> Oh... dammit. I'm guessing ATI's Catalyst is a better performing option than the open source driver though, for Compiz and shading and whatnot. So far.


This is true, the open source driver for the r800 chip is still only young, but it does offer triple head support for eyefinity. And is under heavy devlopment.

> **cascade9 said:**
> LOL, nope. AMD/ATI 6XXX STILL has no offical support, nvidia doesnt drag that much. Also, AMD/ATI XvBA is buggy, nVidia VDPAU works well.

The 6xxx series cards use the same driver as the 5xxx series even in windows, so what more official support do we need? XvBA might be buggy but but VAAPI works very well with the 5xxx series and the 6xxx series in my testing.

---

### Post by cascade9 on 2011-01-14
> **tehowe said:**
> [http://www.xbitlabs.com/articles/memory/display/phenom-ii-x6-ddr3-2000.html](http://www.xbitlabs.com/articles/memory/display/phenom-ii-x6-ddr3-2000.html)

For myself, I guess I'm cuttnig a few corners on my 'dream' machine. When it comes to RAM, though, after reading through the real-world tests, I'd advise people to just go with the 1333 and "save your money"


I thought this was 'dream box' not 'get whatever is cheapest'? 

For a 'dream box' get as fast as possible IMO. Even if you cant 'use' the full rated speed, you can drop CAS ratings at slower speeds. I'd stil say go for at least DDR3 1600 even if its a 'normal' build. It doesnt cost that much more than DDR3 1333, and almost all the cheap DDR3 133 is CAS 9 as well. 

I'm actually pretty familiar with that test (damned dsylexia, I misread '2000'). The only issue is that like most benchmarking it tests things one program/application at a time. The extra memory bandwidth from faster DDR3 is going to help more with multitasking than on a single program. 

> **0004tom said:**
> The 6xxx series cards use the same driver as the 5xxx series even in windows, so what more official support do we need? XvBA might be buggy but but VAAPI works very well with the 5xxx series and the 6xxx series in my testing.

Windows has nothing to do with it. There are drivers for ATI AGP HD cards with windows, none for linux. IIRC the AGP HD windows drivers are given the same revision number as the 'normal' PCIe cards, but its a differrent driver. 

You want to use the ATI 5XXX drivers on linux? Sure, go ahead, but if there was 0 possible problems with them, dont tyou think that ATI/AMD would have released them for 6XXX? 

XvBA is buggy, and from my limited experience VAAPI doesnt drop CPU anywhere near as much as VDPAU.

---

### Post by Grenage on 2011-01-14
While many people are all about the ATI love, I think that their ATI support is bilge.  I wouldn't consider anything other than Nvidia for the time being.

---

### Post by tehowe on 2011-01-16
> **cascade9 said:**
> I thought this was 'dream box' not 'get whatever is cheapest'? 

True dat. Though I guess there's some semantics involved, as paying more than what I did would be more a nightmare ;)

I just wanted to drop a final message here as an update on my install. It could have been my fault in some way, but I just couldn't get the graphics going on UbuntuStudio 10.04 LTS. That's by trying - in order (and using the best resources I could find online to help purge the drivers in between tries) 1. the Radeon driver from the AMD website 2. the proprietary driver offered by the Ubuntu system (Jockey), and 3. the drivers on the PPA offered by the Linux Unofficial AMD Community website. So +1 for Nvidia, or -1 for my hardware combo, whatever the case may be.

However, installing Ubuntu Studio Maverick 10.10 worked out of the box once I let it drop in the restricted driver using Jockey. (Eg; the one the system offers you when you try to turn on enhanced desktop graphics). So if anyone out there gets the same rig as me, unfortunately you may have to skip the 10.04 LTS. But Radeon is redeemed with 10.10 - the 5850 works, anywhow, and it runs the Unigine demo at 15.3 fps with on the 1920x1080 'extreme' setting and 17.3 on 'normal'. :) So if you want a pretty nice machine, this kit works.

Which means things should get interesting in 2012 when 10.10 support expires and I need to figure out how to upgrade my dual-boot setup using the update-manager (do I risk it?) or do an installation over the Ubuntu partition using the DVD, but I guess we'll cross that road when we come to it, armed with some big thick manual on grub.

[Minor peeves: the stock Phenom II 1090T CPU fan runs like a banshee. Hopefully there's a way to tune it down natively, the Windows mobo drivers are quite nice for doing this automatically I noticed.]

Here's a couple pics, thanks all for your help.

[IMG]http://i1107.photobucket.com/albums/h395/tehowe42/IMG_8344.jpg[/IMG]


[IMG]http://i1107.photobucket.com/albums/h395/tehowe42/IMG_8347.jpg[/IMG]

---

