---
title: "Using Ubuntu with New Hardware, overclocking, etc."
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by bflanders on 2007-06-26
Hi all,

I am a longtime Microsoft Windows user ... BUT I REFUSE TO USE VISTA! *I"m movin' to Ubuntu!*

Anyway... I'm planning to build a new system, I want to make it a fast machine that will last a few years. Planning Quad-core (q6600), nVidia SLI MoBo, 4GB ram, 4 good-sized SATA drives in raid 0/1 configuration. Plan to overclock it a bit for that extra OOMPH (Oh.. oh my .. pretty hot!).  I also want to run one or more VMs for WinXP, but want my host OS to be Ubuntu.

That said, I've built machines before, but lately have just bought Dells and such. I've never built an overclocked machine, but it looks pretty simple -- get the right parts, adjust some settings, and poof -- it works.

Here's my problem. There's a deluge of info on the web about MoBo's, overclocking, etc.There's a tsunami of of information about Ubuntu. There's even an ocean of references to overclocking mobo's on ubuntu. I've drank a lot, but can't find that one clear cup of water describing a good buildout for a reasonably fast quad core machine that will run well with Ubuntu. **Enuf with the water references already! :p **

So.. do you all have any links to suggested buildouts for an Ubuntu-friendly machine like this? Any help would be appreciated.

Viva Ubuntu!

---

### Post by hardyn on 2007-06-26
> **bflanders said:**
> 

That said, I've built machines before, but lately have just bought Dells and such. I've never built an overclocked machine, but it looks pretty simple -- get the right parts, adjust some settings, and poof -- it works.



thats really the trick isn't it... if that were the case, it would be called clocking, not over clocking.
you are really going to have to weigh the benefits of a minor boost due to the overclock, versus the lost warranty, added heat, loss of stability, and possibly hardware damage.

most overclocking is independent of the OS; and is usually done with motherboard setting alone.  read the guides that pertain to your hardware configuration. and give it a try if you wish; but do not be surprised if you get random crashes, erratic behavior, no-boot conditions etc.  its part of the game with overclocking.

is there any reason to think that your proposed machine will not be fast enough without oveclocking?  maybe buy a faster CPU instead?

---

### Post by bflanders on 2007-06-26
> is there any reason to think that your proposed machine will not be fast enough without oveclocking? maybe buy a faster CPU instead?

Good point. Maybe I said that OC word too often. From what I've read, if you have good cooling, you can do moderate overclocking of the q6600 with good results. If I found my system failing, I would revert. In any case, I'm not looking to go extreme, just push it a little harder. The more expensive CPU's (qx6700, qx6800...) are not just a little more expensive... more like twice the q6600 at newegg.

In any case, I'd like to buy Ubuntu-friendly parts that others have tried successfully. 

Thanks for the response. 

Best regards,

-- Bob

(Oh.. what hardware do you run?)

---

### Post by dabl on 2007-06-26
What you want to do, bflanders, is what I just did 6 months ago, with about the same amount of trepidation, too.  Here's how I reasoned:  "I'm going to have a helluva steep learning curve to get a handle on Linux, better stick to the standardest hardware I can find."

I got an Intel D975XBX motherboard -- paid a little more, but it's got the Intel HDA audio system integrated, so you can skip a separate soundcard.  The chipset and motherboard has zero issues with (K)Ubuntu.  Get an Nvidia graphics card, so you don't have to go to ATI University to get a functional GUI.  Get WD Raptor SATA drives -- they're great and not too expensive at Newegg these days.  I put 4 GB of Mushkin redline DDR2 RAM in mine.

I got a big airy Antec case with 3 fans in it, and a 650 watt Antec PSU, so I never have to think about power or heat.  I found probably the last Samsung SyncMaster 1100MB monitor -- but the new widescreen LCDs are pretty nice, too.

I put a little WinXP partition on one of the SATA drives, where my Intel BIOS utilities live.  I overclocked my Core 2 Extreme from 2.93GHz to 3.3GHz, and it's been very happy and only gets hot when I get both cores busy encoding audio files. I bought an Arctic Freezer Pro CPU fan -- it's far better than the Intel junk that comes with the CPU.

I hope this gives you some helpful insights.  :)

---

### Post by Yoooder on 2007-06-26
My advice:  Build a machine with good Linux compatible components, and don't worry too much about the overclocking.

Overclocking a high-end quad-core machine will give you bragging rights and perhaps some performance gains--but probably not enough to really warrant it.  

Look at Ars Technica's God Box or Hot Rod for some fairly solid advice on hardware components.
[http://arstechnica.com/guides/buyer/guide-200706.ars/3]("http://arstechnica.com/guides/buyer/guide-200706.ars/3")

---

### Post by Yoooder on 2007-06-26
...one other thing...  don't think that you have to have top-of-the-line hardware to run Ubuntu, even with the 3D desktop effects and tons of goodies Linux can run on a relatively modest machine.

Vista may require 4GB of RAM to hit its "sweet-spot" but 4GB of RAM on a Linux machine will be above and beyond.  I'm not saying to not go high-end, just wanted to make sure there's no misconceptions that high-end is required.

Remember, Linux/Ubuntu is built quite well, and in small incremental pieces (the hundreds/thousands of apps that build into a Distrobution) whereas Vista was built in a year or two as the result of multiple failed attempts--and as such I'm sure that "getting it done" didn't focus very much on making it efficient.

---

### Post by bflanders on 2007-06-26
dabl,

Thanks! Really appreciate it.

I'm looking at the new Antec P182 or P190 case.

Also looking to do Raid 0+1 using 4 250GB or 500GB drives.

Also, thanks for the tip about the audio card.

-- Bob

---

### Post by bflanders on 2007-06-26
Yooder, 

Thanks.

Great advice. I only want the quad-cpu for VMming and still having something left over for the host OS.

(Wouldn't mind a bragging right either!)

Best regards,
-- Bob

---

### Post by hardyn on 2007-06-26
make sure you get a heck of power supply for that many disks!

---

### Post by hardyn on 2007-06-26
> **bflanders said:**
> Good point. Maybe I said that OC word too often. From what I've read, if you have good cooling, you can do moderate overclocking of the q6600 with good results. If I found my system failing, I would revert. In any case, I'm not looking to go extreme, just push it a little harder. The more expensive CPU's (qx6700, qx6800...) are not just a little more expensive... more like twice the q6600 at newegg.

In any case, I'd like to buy Ubuntu-friendly parts that others have tried successfully. 

Thanks for the response. 

Best regards,

-- Bob

(Oh.. what hardware do you run?)


that is usually how i buy processors, buy to the point of diminishing return then do an ebay upgrade in 1year at 50% the retail price; your computer is a toy... and they are fun to upgrade.

what do i run...

an Asus Z71vp 15.4" (1680x1050) notebook with a 2.1Ghz P-M / 2GB ram / 120GB 5400rpm seagate hard disk / and nvidia 6600go/128 video 

I have had various desktops over the years, but i don't think that i will ever return to one ('cept a mythTV box, but that doesn't really count)... i have a dual monitor setup with notebook and run another 500gb of external storage.

---

### Post by Yoooder on 2007-06-27
> **bflanders said:**
> Also looking to do Raid 0+1 using 4 250GB or 500GB drives.

If those 4 drives are identical, you should consider using RAID 5.  You'll lose the capacity of 1 drive (so it will be like 3 drives) but you can redundancy if one of the 4 should die on you.  RAID 5 will protect only against a single drive failure, but with 4 drives you have 4x the chances of that happening.

Also:  I've been building PC's for $$$ on the side for years, and experience has taught me to _always_ include a good battery backup.  A good surge protector will only cover about half of the possible power issues a PC will face, and investing a couple hundred in a good battery will prevent you from spending much more replacing items (not to mention potentially lost data).

For a machine that large you'll want a higher-capacity battery.  I'd guesstimate a 1500 should be reasonably priced and provide you with enough battery to run for several minutes.

---

### Post by Yoooder on 2007-06-28
**FYI: Intel Core 2 bugs!!!**

Just for your, and everyone else's awareness, there is quite a stir being raised about Intel trying to fix a large number of severe issues with a wide range of Core 2 products.  It seems they have been quietly working with MS and BIOS manufacturors to fix as much as possible, however from the sounds of it there are some very serious/exploitable issues that will not be possible to be fixed (ie: severe hardware flaws).

Here's a slashdot article that links to a BSD developer who's been trying to determine all the bugs, and get fixes in place:
[http://hardware.slashdot.org/article.pl?sid=07/06/28/1124256&from=rss]("http://hardware.slashdot.org/article.pl?sid=07/06/28/1124256&from=rss")

---

### Post by dabl on 2007-06-28
> **hardyn said:**
> make sure you get a heck of power supply for that many disks!

That's good advice.  I'm running 1 PATA/IDE, and 2 SATA drives on my rig.  First I blew up a 450-watt PSU, then I ran out and bought this one, which has been going strong for 6 months now: [http://www.newegg.com/Product/Product.aspx?Item=N82E16817371001](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371001)

---

### Post by SoulinEther on 2007-06-28
Uhh... yeah, quard core alone should be way more than enough for what you want to do... don't bother overclocking it.

What could you even do in linux that would require fast CPU performance? lol. Converting audio and video 1 minute faster isn't worth the warranty.

I'm actually looking into UNDERCLOCKING (see [http://en.wikipedia.org/wiki/Underclocking](http://en.wikipedia.org/wiki/Underclocking))... Apple TV does it. I might do it to make a small system (with no fan) using a big CPU slowed down (like a pentium 4 >3ghz slowed down to about 2ghz). Or something. Dunno.

---

