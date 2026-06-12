---
title: "Designing and building a dual-boot PC?"
date: 2008-06-08
forum: Hardware
---

### Post by The Cosmic Hobo on 2008-06-08
I've been away (from both Ubuntu and these forums) for almost two years, due to being restricted by some Windows-specific software and the need to use a laptop (both related to my degree); I thought about trying to set up a dual-boot but never got around to it.
However, my studies are now over. I'm free, and very much in the mood to do something I've not done since 2002: build a new PC and grab myself a decent OS to go with it. I know how to put one together, but that's where my knowledge ends right now. In the six years since I did any building, hardware spec has moved on a lot, and my knowledge has become stale. So, I'm asking for the help of the community.

What I plan to have is:
[LIST]
[*]a *buntu distro as my primary OS (recommendations welcome!)
[*]Windows XP Pro (32 bit) as my secondary OS, primarily for gaming
[/LIST]
across two hard disks, partly for filesystem reasons. I'm also considering partitioning the XP HD for common data storage, if I should feel the urge to go "backwards" or if I find that, say, my digital media player doesn't like Ubuntu.
So what I need, basically, is recommendations for building a good solid system that will last a while and is built from Linux-friendly components - readily available drivers, and such. My HP printer-scanner combo is compatible, so I'm keeping it - anything else, I'm taking the clean-slate approach, as the available parts I've got are 6-10 years old (trusty old SoundBlaster!), not compatible with current standards (IDE HDs, VGA-socket TFT monitor, AGP graphics card - that's about all that'd be useable), or woefully underpowered (about a gig of PC133 RAM).

This is a total build, so I'll be looking for a case and all the trimmings (PSU of suitable wattage, fans and such) as well as a good optical drive, motherboard and processor (I gather they're all dual-core these days - but is there a difference between 2x32-bit processors in one chip and a 64-bit processor?), memory, sound, graphics, wireless networking, a monitor... all the usual. I'm not planning to be a heavy gamer, though I do miss gaming - my laptop really wasn't designed for it, and at the grand old age of almost 5 it's coming to the end of its life, hence building its replacement. On the other hand, I do want to start dabbling with Blender and have the capacity to indulge in my other major interest - independent film-making. It would be nice if the final product were fairly sleek and easy on the eye, not too large, and very quiet.

Any and all offers of help and advice are gratefully received. Bonus points for explaining spec in layman's terms, for advice on making the best job of putting it all together (how do I avoid getting cables all over the place?), or for recommending UK-based retailers. Budget isn't a major consideration but I'd like to keep it around the £1000 mark, excluding the monitor. I'd rather have reasonably-priced, reliable, and reasonable specification than bleeding-edge and unstable, so a little future-proofing is required, and I'm prepared to pay for quality parts.

So... any thoughts?

---

### Post by ardvark71 on 2008-06-08
Hi...

You mentioned you haven't built a system since 2002...I would recommend if you're wanting to build a system with brand new parts that you do some research into the newer technology to make sure mistakes are kept to a minimum. 

As far as the parts themselves go, get a motherboard that has NO onboard anything to where you have complete choice over the other devices. That is always my rule of thumb. And get parts from companies that have been good at offering Linux/Open Source drivers. A Nvidia graphics card is very good choice and from what I'm hearing, Intel is good in that department as well, although be flexible when choosing a motherboard.

Your Sound Blaster card *should* work depending upon the model as well as your printer.

As far as the Ubuntu version, I would suggest 7.10 for right now until 8.04 gets the bugs worked out. ;)

Hope this helps...

Best Regards...

---

### Post by The Cosmic Hobo on 2008-06-08
Thanks for that. I'm actually working on researching new hardware spec right now so it's very difficult. Thought I'd build it this week, and then whoosh!, the rug got pulled from under my feet.

The only reason I felt like upgrading the sound card is it literally supports stereo speakers only. I know it works fine, as I've run a live CD on it - just thought that after ten years it was time for a change :) The printer (and incidentally, my camera) work just fine, so that's another big check-mark on the list.
I'd heard about Nvidia graphics drivers being better-supported. I also noticed there are Nvidia motherboards out there.

I'm going to keep researching and making notes, and my theory is that I can do this through iterative design - find a spec I like, list the parts, check Ubuntu compatibility, re-source/re-spec for non-compatibility, check Ubuntu compatibility, cost, re-source/re-spec for cost... you get the idea :)

I did consider just buying a Dell with Ubuntu pre-loaded, but in my experience the customer service isn't so great. Besides... I love to tinker with things ;)

Thanks once again, and hopefully we're going to get a discussion going here. I've got this crazy idea to document the whole process (design, build, install, optimise) to help fellow new folks.

---

### Post by ardvark71 on 2008-06-08
> **The Cosmic Hobo said:**
> 
I'm going to keep researching and making notes, and my theory is that I can do this through iterative design - find a spec I like, list the parts, check Ubuntu compatibility, re-source/re-spec for non-compatibility, check Ubuntu compatibility, cost, re-source/re-spec for cost... you get the idea :)


Hi...

You're welcome! I'm glad to be of assistance. :)

The approach you mention above will serve you well. It should definitely keep mistakes to a bare minimum. ;)

I, too, would not get anything from a manufacturer with Ubuntu pre loaded. Getting your own parts ensures better quality control and compatibility if you want to upgrade in the future.

Although they are not prominent in the market place, AOpen has made quality motherboards and devices in the past, although I can't comment on their products made today. The last system I owned (before receiving my current system) had a old AOpen  AX6BC, made in 1998-99. I upgraded it to a Pentium III and it's still working great today (I gave it to my neighbors,) even after having it run almost everyday for four and a half years, not counting how it was run before I got a hold of it in 2003. :D

Best Regards...

---

### Post by xjgnsdof on 2008-06-08
Half the fun of building a PC lies in researching the parts yourself, but I can give you some pointers, as I built a dual-boot gaming PC the day Gutsy came out, coincidentally

--Hardy Heron doesn't have more bugs than any other Linux distro. Suspend and hibernate are hit-or-miss, as usual.
--Wireless support has vastly improved: Hardy detected my Broadcom card by default, and it also detected my Linksys wireless adapter. In my mind, desktops should always be plugged in through an Ethernet cord.
--I assume you want to play PC games on your Windows partition. If so, you'll want to run NVClock while you're in Linux to boost the fan speed on your gaming cards. I use an 8800GTS512 and set NVClock to change fan speeds at startup.
--RAM, monitor, sound card, etc. will probably be compatible no matter what *buntu distro you pick

---

### Post by The Cosmic Hobo on 2008-06-08
Thanks!
I agree, the fun is in the researching. However, I'm that out of date that I feel genuinely lost, hence the asking. But I'm getting there :) Been looking at retail systems this morning to get an idea of what spec to aim for.

As for playing Windows games - I was going to simply boot into Windows to play them, but after reading your post it occurs to me that I could set up an emulator or an application layer (like Wine) to run under Linux. Is that what NVClock is for?

I also agree about wired v wireless - I've always found ethernet to be much more reliable than 802.11, plus there's less startup lag, better connection security, etc. However I'm not in a situation where I can run cabling all around where I live, so I'll have to stick with what I can get for now. When I've got my own place and my router can be in the same room as the PC, though... :)

---

### Post by The Cosmic Hobo on 2008-06-08
A quick update:
Unless there are any serious issues with it, I think I'm going to use a [Nvidia GeForce 9600 GT](http://www.bit-tech.net/hardware/2008/02/21/g94_nvidia_geforce_9600_gt_graphics_card/1) as my graphics card. I'm tempted to get two and SLI-link them, but I don't plan on doing anything that intense just yet, and it'll probably be a Windows gaming thing if I do. Not sure if there are any benefits to dual graphics cards or SLI under Linux.

I have a shortlist for the sound card, and after that I think motherboard and processor. I'm eyeing up some LightScribe-compatible optical drives, which I believe have Linux applications available. Hard drive and RAM should be fairly easy, the monitor hopefully won't bust my budget... the real toughie will be the case, working out the PSU spec I'll need, and things like quiet cooling kit! :mrgreen:

But yeah... the research is tons of fun :) Thanks for the info so far, it's coming along nicely.

---

### Post by xjgnsdof on 2008-06-09
I'm all for SLI, especially if you plan on running games in WINE or encoding a lot of video.

NVClock is a Linux equivalent of RivaTuner. Without it, your card(s) will run at default fan speed, which is normally lower than 50% of maximum speed. This is good for electricity consumption and noise, but bad for performance.

Post your shopping list once you create it.

---

### Post by tubbygweilo on 2008-06-10
Following the open source mantra of Ubuntu I wonder if you have considered selecting something that works with [coreboot]("http://www.coreboot.org/Welcome_to_coreboot")? 
That way you could be open source from bios right through to applications:)

---

### Post by The Cosmic Hobo on 2008-06-10
One shopping list coming up!
I think all this should work together pretty well. Some of the brands I'm unfamiliar with - an American friend tells me MSI are very reputable and good quality, though, so I'm trusting them. I've tried to make sure that the motherboard specifications match the graphics card, and that the RAM will give best performance, and so on.
Any really obvious blunders, I'd appreciate hearing about.

Oh, and the model numbers in the list below are clickable for specs and such.

[LIST]
[*]**CPU:**Intel Core 2 Duo 3GHz socket 775 1333FSB. Either the [E8400](http://www.dabs.com/productview.aspx?Quicklinx=4YCZ) (which is cheaper, manufactured to 45nm, has a 6mb cache, and has Trusted Execution) or the [E6850](http://www.dabs.com/productview.aspx?Quicklinx=4MM7) (which is manufactured to 65nm, has a 4mb cache, and has Advanced Smart Cache).

[*]**Motherboard:** MSI [P7N Diamond nForce 780i SLi](http://www.overclockers.co.uk/showproduct.php?prodid=MB-098-MS)

[*]**RAM:** This one was tricky, because a couple of RAM check sites didn't have this listed. One of them gave me the DDR3 chip, which I don't think that motherboard supports. So I've checked manually, and found a couple of possibilities: 2x2GB DDR2-1066 sets from [Crucial](http://www.crucial.com/uk/store/partspecs.aspx?IMODULE=CT2KIT25664AA1067), [Corsair](http://www.overclockers.co.uk/showproduct.php?prodid=MY-148-CS) and [G.Skill](http://www.overclockers.co.uk/showproduct.php?prodid=MY-023-GS).

[*]**Graphics:** MSI's GeForce 9600 GT, in either [512mb](http://www.ebuyer.com/product/143552) or [1gb](http://www.ebuyer.com/product/145005) flavours. I've not seen much about the 1gb, but the 512mb apparently draws just under 300w when benchmark tested, and just under 400w for the same test when SLI-linked.

[*]**Sound:** The motherboard I've picked out actually comes bundled with a sound card (unusually - but it has no onboard sound or graphics). I've also picked out two PCIe cards as possible upgrades - the [Asus Xonar DX8.1](http://www.overclockers.co.uk/showproduct.php?prodid=SC-002-AS) and the [Creative SB X-Fi Xtreme 7.1](http://www.overclockers.co.uk/showproduct.php?prodid=SC-052-CL).

[*]**HDD:** 2x [Seagate Barracuda 7200.1 500gb 7200rpm S300 32mb](http://www.dabs.com/productview.aspx?Quicklinx=4QXH). Used Seagate before and never had a problem with them. 1tb might seem excessive but I want to keep my dual boot OSs separate and have space for shared data, backups, space-hungry game installs...

[*]**FDD:** Retrogaming is a hobby, so I figure I'll need a floppy drive at some point for disk images I just can't get anywhere else. Looks like that motherboard doesn't have a FDD slot, so I'll grab a USB external at some point.

[*]**Optical:** DVD rewriter, no question of it. Not strictly necessary, but I like the idea of being able to use Lightscribe on certain things (archives of downloaded podcasts, free-to-download independent films and fanfilms). I found the [LiteOn LH-20A1L](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=775022), which is reasonably priced. Been using LiteOn drives in my last build and never had a problem with them, but there are plenty of alternatives.

[*]**Wifi:** No choice at the moment, so I'm looking for a PCIe ethernet card. Failing that I can get a USB dongle, or recycle an existing PCI card.

[*]**PSU:** No idea how to spec this correctly, but I've been guessing 600w should do the job. This [CoolerMaster RealPower M 620w](http://www.aria.co.uk/Products/Components/Power+Supplies/500w+%2B/Cooler+Master+Real+Power+M620W+Modular+Power+Supply+?productId=30605) looks like it should do the job, but advice on good makes and if I've got sufficient power would be great. I've also seen the [Tagan Modular BZ Piperock 600W](http://www.aria.co.uk/Products/Components/Power+Supplies/500w+%2B/Tagan+600W+Modular+BZ+Piperock+Series?productId=30955) as an alternative.
[/LIST]

I've already got a great Linux-compatible printer, and a pair of stereo speakers in storage (I do want to upgrade to something better, but for now those are fine), so all I really need to find now is a good monitor, a case, and a couple of peripherals. I'm tempted to casemod, but I'll gladly settle for something simple, sleek and stylish. Had my eye on the [CoolerMaster Cosmos 1000](http://www.dabs.com/ProductView.aspx?Quicklinx=4QXL&CategorySelectedId=11023&PageMode=1&InMerch=1) - that doesn't really need anything like cold cathodes, and is quite nice as-is (though I saw a modded one in a magazine - gorgeous case, tons of room to work inside). I might try to source some cable sheathing to keep the inside tidy, though.
Oh, and a cooling system - mustn't forget a CPU cooler and some fans. Contemplating liquid-cooled, but not sure how good an idea that is, especially with a move coming up in the near future.

So, there it is. Any glaring errors? Any poor choices of brand? Is the PSU underpowered? Got any better suggestions? Any suggestions for a good monitor would also be appreciated. Once the spec is writ in stone I'll start shopping around for good prices, and keep the forum updated on the build and install.

Hope it fulfils my aims though - sleek, simple, moderately future-proof, reliable, Ubuntu-friendly...

***Edited to add:***
> **tubbygweilo said:**
> Following the open source mantra of Ubuntu I wonder if you have considered selecting something that works with [coreboot]("http://www.coreboot.org/Welcome_to_coreboot")? 
That way you could be open source from bios right through to applications:)
That sounds absolutely fascinating. I'll look into it, though I think at the moment it may be beyond my technical ability.

---

### Post by Curtisc on 2008-06-10
You might be surprised at the power requirements - since the P4 days, especially with the E8400 CPU (very low power), they've come down a fair bit.  Check out [http://extreme.outervision.com/PSUEngine](http://extreme.outervision.com/PSUEngine) and then add a decent safety factor.

I know five people who have built computers in the past year or so (including myself last Thursday!) and the case that everyone went for is the [Antec Sonata III](http://www.overclockers.co.uk/showproduct.php?prodid=CA-073-AN).  It's really well laid out, fairly compact, very quiet, and it comes with a pretty decent EarthWatts 500 W power supply, which should be plenty for your system (although if you go SLI in the future that might have to be bumped up a bit).

Also, if price is a factor I might suggest looking at DDR2-800 ram.  I'm not sure that the performance benefit is quite worth the price difference between 800 Mhz and 1066.

As far as liquid cooling and such goes, once again, the processors they're making these days aren't anywhere near the power-sucking heat-producing monsters of six years ago.  Unless you're overclocking or you want complete silence, the stock fan and heatsink that come with the cpu should be fine.

For monitors, I'm partial to Viewsonic, but that's probably one of the most "personal preference" based things.  Definitely look at at least a 20" widescreen.  I think 20" is the perfect size, because it's usually the same resolution as the 22" but higher pixel density (and you can get non-TN based panels without paying a fortune), but probably the best would be to look up a few monitors online and then go to a computer store and see how much you actually like them (if you can find a shop that has monitors on display that aren't attached to a 16-way split VGA cable).

My 2 cents... a lot of this stuff really comes down to personal preference, and I don't think you could go wrong with the system as you've got it there.

---

### Post by The Cosmic Hobo on 2008-06-10
Thanks for that.
It's hard catching up on six years' difference in tech. Budget is no object with my build, but it's tough trying to figure out whether matching RAM speeds to what the motherboard can do is beneficial or not - the same as I'm not sure if a 1gb video card is better than 2 512mb video cards, or if a dual-core processor and a 64 bit processor are different things. It's a long job, and you'd be surprised at how far I've come since last week, when I started thinking about treating myself to an iMac as a grad present.

I'll take a look at those links. Don't plan to overclock, but nor do I want what I got with my last build (which sounded like a Harrier jump-jet taking off), despite paying for "quiet" PSU and fans. The CPU doesn't say it comes with a cooling fan, but I guess they're not too expensive if I need one. I think the last one I bought did, though, and I wasn't planning on messing around with HDD coolers, RAM coolers, slot-on GPU cooling sleeves, or anything like that. I remember I liked the look of Zalman flowers a few years back, though. Probably as well to stick with what works and noddle around with it later, eh?

As for monitors, cases and brands - yes, definitely personal preference :) but I'm out of the loop. You've probably noticed that there are a couple of instances where I've said on the list that "I'm using this brand because I used it before and had good experiences". Monitors... you're probably right, I should find somewhere I can check them out. Might be worth a walk up PC World, even if I can get better prices online, just to see how they act.
That Antec is gorgeous, though. A lot cheaper than the CoolerMaster, too. If I need a PSU over 500w I can always upgrade later (and right now I'm considering just one graphics card; I can always add SLI at a later date). All it needs is an Ubuntu case badge ;)

Anyhow, nice to have another two cents on the pile, and thank you! It's reassuring to know that I've got a good system spec there. It might be a tad overpowered for Ubuntu, but I'm sure XP will make light work of the extra capacity (as I understand it, XP won't even recognise over 3gb of RAM, so...).

---

### Post by Curtisc on 2008-06-10
> **The Cosmic Hobo said:**
> Thanks for that.
It's hard catching up on six years' difference in tech.
It sure is.  I played the same game last week, and it took a lot of reading.
> **The Cosmic Hobo said:**
> Budget is no object with my build, but it's tough trying to figure out whether matching RAM speeds to what the motherboard can do is beneficial or not
I'm not really sure on this either.  I've heard advice to match the RAM speed to the FSB speed, but with a 1333 FSB processor that's not going to happen anyway.  If budget is no object then you really can't go wrong with faster RAM (I was trying to keep my build under $500, which didn't quite happen, but it came close).
> **The Cosmic Hobo said:**
>  - the same as I'm not sure if a 1gb video card is better than 2 512mb video cards, or if a dual-core processor and a 64 bit processor are different things.
I'm not into gaming, and I'm not sure how much more complicated it would make X configuration, but it seems like 2x512mb would be miles ahead of 1x1gb.  From what I've heard though, the 8800GT is still the reining champion of bang-for-the-buck - it's more expensive than the 9600GT, but according to [Tom's Hardware](http://www.tomshardware.com/reviews/graphics-cards,1942-3.html) it "beats the ... 9600GT by a notable margin".

All of the intel dual- or quad-cores are 64 bit processors.  If you're planning on putting 64-bit Ubuntu onto the new machine, you might want to check and see if there are any compatibility issues with programs that you need.  I stuck with the 32-bit version to prevent any surprises, but that was mostly just laziness.  Also remember that in order to see the full 4gb of ram, you'll need either the 64-bit version, the server kernel, or a custom compiled kernel (I haven't done this yet, also out of laziness and the fact that 3.2gb hasn't come close to getting filled).
> **The Cosmic Hobo said:**
> It's a long job, and you'd be surprised at how far I've come since last week, when I started thinking about treating myself to an iMac as a grad present.
Building is way more fun ;).  I don't think it's overpowered at all - just because Ubuntu *can* run on more modest systems doesn't mean that it can't take full advantage of this kind of power.  It's pretty awesome turning on a computer and booting up in less than thirty seconds.

I too would like to get a case badge... can't seem to find them anywhere though...

---

### Post by The Cosmic Hobo on 2008-06-10
Well, thanks again for the input. I'll give that some thought - I know nothing about compiling custom kernels, so that's made me a little wary. It's probably idiotproof terminal stuff, so I shall do some asking around. Ditto for configuring X to accept SLI. The graphics cards... I hadn't considered going lower-end, but I heard today that the 9 series drivers were less than optimal, so again, food for thought.
As for a case badge - there were, apparently, some available at the end of last year, but they all sold out. There are a couple of stores selling Tux badges, but no Ubuntus that I can find.

---

### Post by Enroth on 2008-06-10
"(as I understand it, XP won't even recognise over 3gb of RAM, so...)."

I'm not entirely sure on this (its been a while since i read up on this), so if someone can back me up here (or flat out tell me I'm wrong) this problem is not contained to XP, it is to do with a 32bit systems, so all operating systems are affected by it including Ubuntu (Unless you are using a 64 bit system). This is to do with memory addressing, with no more than 2^32 address available (or something like that). Of course if you want more RAM to work you will need to swap to a 64 bit system (includes 64 bit processor, operating systems that use it etc (here is where i start to know nothing, I'm not sure how this affects things like windows installs, or just ordinary programs being run)). 
This 3gb not only includes your memory sticks but also the RAM included in your graphics card.

Like I said though it has been a while since i read up on this, so don't take my word alone.

---

### Post by molotov00 on 2008-06-10
I'm in a similar position. I recommend MaximumPC.com. I don't read it regularly but:

 - Lots of info about new technology and ideas for builds
 - Legit FREE PDF downloads, identical to news-stand versions

---

### Post by The Cosmic Hobo on 2008-06-11
Ah. NOW I understand the casual comment about XP not recognising large amounts of memory... processor addressing. Also explains why I was told I may need a 64-bit kernel. I could scale the memory down to 2gb for starters and upgrade later once I know how to compile and such.

---

