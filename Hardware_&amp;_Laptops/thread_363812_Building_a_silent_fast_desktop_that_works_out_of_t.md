---
title: "Building a silent fast desktop that works out of the box."
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by Gallog on 2007-02-17
OK I have been searching the ubuntuforums for a while now and I can not find a good answer for this. I want to build a silent, fast and ubuntu compatible desktop. So I have a couple of random questions that would help me build my new desktop.

I heard Core 2 duo is the best CPU right now, is this true? Do you have any better alternativs.

It seems like many of the motherboards supporting the Core 2 Duo does not support PATA in ubuntu. Something wrong with grub andhas it been the controller. Is this true or  has it been solved?

I've been looking at the Asus P5W DH motherboard. Has anybody got this motherboard working out of the box?

What is the best setup on HDD:s? What about RAID? What HDD:s to buy? SATA, IDE? Size?

Does anybody know about any cool cases?

What about screen? 23'? TFT?

It would be cool if someone had a list of a below $2000 desktop with nice features making it fast and noiseless.

I am not a gamer so a nvidia card letting me run Beryl smooth would be enough.

Any advice on putting a new desktop together is appriciated.

---

### Post by Daveth on 2007-02-18
Antec make good cases, though they are not cheap. Lots of room inside and, in the P180, a physical separation of psu and motherboard. Uses quiet 120mm fans which whoosh along nice and quiet. Not something you want to try lugging around the house though. You need to replace the stock cooler fans on Nvidia cards- Zalman make excellent and quiet ones which are easy to fit. And do not forget to replace the stock cooler on the cpu - for AMD this is an easy job. Choose a quite and reliable psu, I use a Seasonic 600. Motherboard choice should be informed as much by cpu choice as whether it supports some passive cooling- Northboard passive cooling cuts out 1 more fan to scream at you.
Core 2 are fast and Intel has played catchup with AMD, though I still rate the Athlon 64 x2s, especially the 939 whose price plummeted with the advent of the AM2 socket. Not sure what others may think but it seems that with linux that being too cutting edge might leave you with work to do to get things running, whilst being trailing edge seems just fine.
If you really wanted to be quite there is always water-cooling of course!

---

### Post by the ev on 2007-02-18
**In regards to cooling**

> **Daveth said:**
> If you really wanted to be quite there is always water-cooling of course!

Yeah, one-step shy of the ultimate in silent computing would be to water-cool your system with a passive radiator.  Zalman would be my first choice for a passive cooler.  You can then get waterblocks for pretty much any CPU you decide to put in there, with waterblocks for your GPU as well (if you get a card with an onboard fan).  The only downside to a passive cooler for a water-cooling system is that it is extra hardware that will sit outside your system, which makes it even less portable or relocatable.  You'll also want to make sure that there's good airflow around it so you can make sure it's doing its job.  You can increase the cooling capacity of the system by getting an extra resevoir too, which you can mount either out of your way inside the case or in a 5.25" bay for some flare (check out Thermaltake's inbay resevoirs and flow monitors).

For motherboards, I know that several boards cool the north and south bridges using heat-pipes and peltier blocks.  For optimal cooling, you should try to water-cool those as well (there are blocks available).  The more cooling to can do through the water system, the less you will have to rely on potentially noisier fans.  Of course, if watercooling is too much, try to find a case that supports 120mm fans, as they run the quietest.  Getting a fan controller and temperature probe would probably be a good idea as well, as then you can lower the fan rpm manually and still keep tabs on internal system temperature.  

Finally, I'd look into getting hard drive enclosures as well. Scythe makes some good ones and good prices (I've been very happy with them so far, but admittedly I haven't owned them for very long), and there's the Nexus Drive-A-Way as well (you can find it at Xoxide.com).  Passive HD cases not only silence the drive, but help cool it and prolong its life as well.  Obviously, avoid HD cases that include a fan (crossblow or otherwise), as this will increase the noise.

I say sub-ultimate solution, because if you've got the money for it, you should look into Zalman's totally noiseless systems; they are totally silent, but also are much pricier.

As for PSU's, I've heard iffy things about passive cooling on them, so I would vouch for one that utilizes a 120mm fan.  I have the Hiper 580W modular that has a 120mm and an 80mm fan and is even SLI rated, and it still runs rather quiet; I'm quite impressed.  That PSU might be overkill for your system, but I just wanted to illustrate how big a difference those 120mm fans make.

**In regards to system innards**

For HD's, I've gone the way of SATAII drives.  They are much, much faster than IDE (3 gigs a second) and are very reasonably priced nowadays.  The cables are physically smaller than IDE cables as well, which will help airflow in your system and keep it cooler.  If you get a nicer motherboard, you can upgrade to a RAID configuration if you decide you need it.  

> I've been looking at the Asus P5W DH motherboard. Has anybody got this motherboard working out of the box?

I don't know about that exactly motherboard, but all the Asus board's I've ever had have worked flawlessly with whatever OS I decided to run.  I currently have the P5N32-SLI Deluxe (can you tell I'm a gamer?), and it has no problem with Edgy.  Asus is my manufactorer of choice when it comes to motherboards; it's hard to go wrong with them.

What motherboard you get, as Daveth pointed out, will depend greatly on else is going in your system, most notably your CPU.  I've had no problems with my Pentium D, and I hear (as you have as well) that Core2 is looking pretty good too.  I know less about AMD, so I can't really comment.  If you're looking for extreme speed on an extreme budget, check out the Pentium D 805 2.66 Ghz.  The chip costs around $120, but remains stable when overclocked to 4.2 Ghz.  Once you get above 3.8 Ghz, though, you'll have to water-cool it.  There are several guides online about how to do this, but I think the best is probably from [Tom's Hardware]("http://www.tomshardware.com/2006/05/10/dual_41_ghz_cores/").  If you do go with a newer Asus motherboard, they have the built-in AI NOS which will allow you to easily overclock the chip and has failsafe capability.  Not bulletproof, mind you, but a step in the right direction.

I would definitely recommend upgrading the stock cooler that comes with the chip.  If you have room inside your case (and are not water-cooling), there are passive radiator towers that offer silent cooling.  These, however, will raise the internal temperature of the case, so you'll need to include more case fans to compensate.  Zalman again makes excellent CPU coolers; I'd recommend them to start with.  

For RAM, Corsair ValueSelect brand is very reasonably priced and performs quite well.  I'd also get cooling plates for them (they just slide over the chip); not only does your RAM now look awesome, but it helps dissapate the heat and keep the chip healthy.  You'll have to be sure you get the right type of RAM for whatever motherboard you select.

Pretty much any nvidia card should work for you, it sounds like.  I have onboard nvidia graphics controller (very standard) on my tablet PC, and it can run Beryl with only a few, slight hiccups, so any dedicated card should handle Beryl just fine.  I would, however, check out Beryl's documentation and other user posts on their forums just to verify that; my only experience with running Beryl on a desktop has been with an Nvidia 7950GX2, which is a monster.

**In regards to system casing/periphrials**

Antec makes great cases, as does Lian Li and Cooler Master.  I have the Cooler Master Stacker 830 and it is oh-so-great.  Top notch quality and durability, and plenty of space to work with.  Lian Li's tend to run a little on the expensive side, but you certainly get what you pay for; I always liken them to the Mercedes-Benz of computer cases, but that's just me.  For easy setup water-cooling, Koolance and Lian Li now make cases with built-in water cooling.  Thermaltake also makes prepackaged cases.  They'll run you a little more, but if you're not comfortable setting up a water-cooling system on your own they might work out better for you.  

As for the monitor, I'm a huge stickler for quality, so I have no qualm about forking out for an Apple Cinema Display.  The 20", though the at the bottom of Apple's product line, is stunningly gorgeous and I have never once regretted that $700.  My friend just got the 23", and he says it is hands-down the best monitor he's ever owned.  The only potential problem is that Ubuntu doesn't seem to like booting if the monitor's built-in USB hub is plugged in (the monitor is also a firewire 400 and USB 2.0 hub, with ports built right in on the back side).  That problem might get fixed with future versions of Ubuntu, who knows, but just be aware of that if you decide to get a cinema display and Ubuntu all of a sudden won't boot.

**In regards to actually building the system**

Most of the parts shopping you'll have to make your own decisions about what to get.  I highly recommend both [Newegg]("http://www.newegg.com") and [Xoxide]("http://www.xoxide.com").  My general shopping habits take me to Xoxide first, to scope out generally what I want, then I try to find it on Newegg, as Newegg generally has better prices and much faster shipping.  Newegg, however, doesn't carry all of what Xoxide has to offer (and vice versa; in fact, Newegg has a much larger inventory, but seemingly fewer specialty items than Xoxide), so be sure to check out both exhaustively.  I've bought from both merchants, and they are both reliable and secure.

If you're paranoid about damaging your hardware while assembling the system, I'd recommend you invest in a static-free matt and wristband; they're dirt cheap and will reduce the chance of static discharge.  If you're recklessly confident that everything will be alright regardless (as I am), then go right ahead and don't spend the extra money...just don't wear any wool clothing while building your system.

If you did decide to go with watercooling, there's a neat little trick which allows you to run the cooler without turning the system on.  My old Koolance Aquian system showed me this, and I've been able to use it on my newer Cooler Master Aquagate with great success.  Bascially, you trip the power supply by connecting the 4th and 6th pin on the motherboard power connector, which starts the supply and provides power to whatever is connected to it without turning the system on, as there's no power going to the motherboard.  I use this all the time when filling up the water cooling system fully, as you have to turn it off and on multiple times to get water throughout the whole system.  Be sure you get the right pins, however, because if you get the wrong ones, you can short the power supply and fry it - which wouldn't be very fun.  If you hold the motherboard connector up so that the click-latch is on top, then count over on the top row starting on the left, the 4th one in and the 6th one in are the two you should connect; and you connect them to each other.  The Koolance unit came with a little cable for expressly this purpose; I don't know if you can purchase them individually - I haven't looked.

Well, my two cents.  Sorry, this post kinda took off and ended up being a lot longer than I had initially intended.  I love building computers, so I get a little passionate about it.  Anyway, I hope all of that was helpful; if you have any questions about what I've wrote here, don't hesitate to ask!  Good luck, dude.

---

### Post by benow on 2007-02-19
Hehe, here I am, searching the forums on how to automatically spin down hard drives (powersaving) for my new silent pc and I stumble onto this...

I've been planning a miserly quiet workstation for a while, as I'm hoping to go mobile and be under solar power (equipped truck camper on 4x4).  I also love music, and the whine of the fans just doesn't cut it.  I've basically dedicated my life to programming and plan to continue doing so, so I need something which is as friendly as possible.  Here's what I came up with (prices are in CDN dollars, 9/10 of US):

- CPU - AMD Athlon 64 X2 4600+ HE - $255 - 2.4Ghz high efficiency dual core processor.  Draws 65W during full processing and cool n' quiet (ondemand) out of the box, so draws ~35W when <=1Ghz processing is suffient (ie most of the time).  AMD make an X2 4800+ @ 2.6Ghz, which is a nice proc, but a bit more expensive.  AM2 socket.  Works fine with ubuntu, cool n' quiet needed enabling in the bios.  I've heard the core2duo is nice, but would not be less power than this, and AMD's done me right in the past.

- MOBO - Asus M2NPV-VM - $99.95 - Flagship mobo, with onboard sound and video, AM2 upgrade path, DDR2 800, quad SATA 2, dual ide, pci-e 16x, 2x pci 2.2, firewire, usb2, hdtv out.  Onboard video is geforce 6 series which shares system ram.  It's not ideal for high performance requirements (ie highest fps is games), but is fanless and quick enough, which is all I care about.  Very good so far.  Works fine with ubuntu, tho I had to manually install nv beta binary drivers (not sure if this is a feisty problem).

- HD - Western Digital Raptor 36G, 10k RPM, 16M Cache, NCQ - $135 - Small, fast system drive.  hdparm -t  of 62M/s.  Basically the fastest solo drive out there.  Big enough for system.  A bit loud, but it's not on much.

- RAM - OCZ platinum DDR2 800 (pc2 6400), 2x1G - $279.95 - fast, cheapest of the expensive.

- COOLER - Scythe Ninja Silent - $60 -  Aluminum & Copper sculpture.  Has fan mount if fan required.  Works fine fanless here.

- PS - Antec Phantom 500W Silent Power Supply - $210 - more than I need, but will last a while.  It's silent, but has a fan which comes on when it needs to (which it never does).  

- MONITOR - Dell 24" 2407FPW - $850 - 1920x1200.  Could go bigger, but they get (more) expensive.  This is not cheap, but it is a fine monitor and will last for years.

Total $1900, expensive, but a fine fine workstation for many years.  The system is eerily silent.  A bit of noise from the HDs when in use, but that's it.  There's a whole spaciousness in the music which comes out... like listening to standalone cd player via headphones, very nice.  When I'm in the forest, I'll be able to hear the birds and streams without washout... yay.

My old system, btw, was a smp tyan opteron 246 box, drew 170W sitting still (no power saving mode) and very loud... heh, a grunt tho.  It becomes a server and the cpus can be upgraded (for a grand) to the mid of current gen... which would be a quad 2.4Ghz orso.  It's not dead yet, and won't be for a while.

The next upgrade is a gigabyte iram, with 4G ram.  It's a solid state ram harddrive.  It draws power from pci, is connected via SATA and the os sees it as a std harddrive.  No seek time and max out SATA 1 (unfortunately, no SATA II model yet).  I'm planning on building a HD cache VFS (virtual file system), which loads files from iRAM, or if not in iRAM, from hd and populate iRAM (MRU cache).  It should speed disk subsystem up at least 100x, and, as I can agressively powersave the hard drive(s) and RAM takes comparatively very little power, save even more power.  If I can get the fs working as a root fs, it should (with a bit of logic) decrease boot time to ~5s orso(!).

From this kit I've learnt that quiet==efficient.  It's very fast, very quiet and (really) very affordable for what you get.

---

### Post by xelink on 2007-02-19
c2d for processor, take your pick
scythe infinity w/o fans for HSF
passive GeForce 7300/7600 for video card, any will do as you aren't gaming

congrats, you no longer have any fans in your case...

---

