---
title: "Best motherboard for linux?"
date: 2009-05-11
forum: Hardware
---

### Post by Psyphre on 2009-05-11
Hi all,

I'm looking to buy a new motherboard because my current one died last night, after years of problems. It was an Asus P5N32-SLI Premium, which worked a dream in ubuntu and was a great motherboard, but it just kept breaking, refusing to boot etc etc on a regular basis.

I think this time it has completely stopped working so I'm looking to get a new one with a price range around £100 (but less is better :)).

What would you recommend? Of course it goes without saying that it needs to be compatible with linux.

One final preference is silence. Passive cooling as I hate using fans.

Thanks alot everyone.

---

### Post by Psyphre on 2009-05-12
bump. No one has any motherboards to recommend at all? :(

---

### Post by VastOne on 2009-05-13
> **Psyphre said:**
> bump. No one has any motherboards to recommend at all? :(

I am very happy with my Gigabyte and Phenom II setup

---

### Post by Psyphre on 2009-05-13
Thanks for the reply. What gigabyte motherboard is it? Does it work 100% in ubuntu?

---

### Post by Malakai on 2009-05-17
Hi guys. Ubuntu 9.04 is running perfectly on the following setup. Any 790GX/FX board will do, I use the Gigabyte MA790GP-UD4H and I LOVE IT!! IMO gigabyte has the best 790 boards on the market right now. Bios layout is perfect, board layout is great, heavy, quality components, great cooling. My board has a heatpiped passive heatsink on the CPU power circuitry too.

Gigabyte also has a great cheap little 790X board for only 100-110, but I like having backup DX10 graphics from the 790gx chipset in case anything ever happens to my HD4830.

Full specs, Phenom 2 really owns. I paid 280 shipped for the cpu and mobo a few months ago, a friend had the ram sitting around and gave it to me!

Phenom II 940BE 3.66ghz(243x15)@1.44v, 2ghz HT & NB | Sunbeam Core Contact
Gigabyte MA790GP-UD4H | Sapphire HD4830 @690/1050 | Thermaltake 550W PSU
8gb(4x2) G.Skill DDR2-1066@972mhz 5-5-5 2.0v | Logitech z-2100e 2.1 Speakers
WD640 Black HDD | 1TB WD Green | Logitech MX518 | MS Natural KB | Antec 300 Case
BenQ G2400WD 24" TN | Viewsonic VP191b 19" | Vista Ult 64-bit | Linksys WRT54GL

Linux works fine on pretty much any hardware out there right now, the question is does the distro your installing have the drivers built in for your setup. 9.04 has all the drivers you need to get started for the 790GX/SB750. Newegg link to my board:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128384](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128384)

---

### Post by Psyphre on 2009-05-17
Thanks alot for the suggestion. I appreciate it.

I just realised that I forgot to mention I've got an Intel CPU, so cant use AMD motherboards.

I'm currently considering the Asus P5Q-E.

---

### Post by c0nfusedami on 2009-05-17
i recently put together a computer with an asrock g43twins-fullHD and it seems to be working alright except for the integrated graphics card however it's not the quietest board

---

### Post by khelben1979 on 2009-05-17
I think that the most important thing is getting a good motherboard when looking at the hardware specifications and how it is built rather than if it works good for Windows or Linux.

Linux should handle most if not all motherboards which is out there. Am I right?

Anyway, DriverHeaven have some good reviews on motherboards [here]("http://www.driverheaven.net/reviews.php?category=5") if you're interested.

---

### Post by logos34 on 2009-05-17
You might also consider getting a mobo that supports LinuxBIOS/CoreBoot:

[http://www.fsf.org/campaigns/supportlinuxbios.html](http://www.fsf.org/campaigns/supportlinuxbios.html)

---

### Post by moster on 2009-05-17
[http://hardware4linux.info/systems/]("http://hardware4linux.info/systems/")

hm, why somebody did not post this before?

---

### Post by Psyphre on 2009-05-17
oh wow suddenly alot of replies. Thanks.
[B]
Confusedami:[/B] Ah shame its noisy. Its really important that I get a nice quiet board with no fans. Thanks for the suggestion though.

**khelben1979:** I wish that were true. Linux _should_ work with all motherboards, but unfortunately that isnt the case. I bought a motherboard for someone before and it would have random lock ups in linux (every hour or so). Other motherboards may require hacking or tweaking to get it to work nicely with linux etc. Things like inbuilt wifi, ethernet ports and so on tend to cause issues.

Ive had alot of comp issues past month so I'm totally fed up, which is why I'm searching for a nice easy board with no headaches.

**logos34:** from the link you gave me, it says not to buy intel. Unfortunately I already have an intel cpu, so ive got to buy an intel board.

**moster:** thanks for the link. Looks quite handy in verifying what mobos work and what dont.

---

### Post by moster on 2009-05-19
I do not understand why developers who actually code drivers into kernel make some list to people see what chipset is actually supported. I would really love to know with 100% certanity what mbo chipsets, wlan cards, etc have 100% support in linux.

If somebody knows something about this, say it.

---

### Post by logos34 on 2009-05-19
> **moster said:**
> I do not understand why developers who actually code drivers into kernel make some list to people see what chipset is actually supported. I would really love to know with 100% certanity what mbo chipsets, wlan cards, etc have 100% support in linux.

yeah, everything concerning linux hardware support is needlessly obscure...But you can always custom compile your own kernel with the drivers/modules you need for your board and peripherals.

---

### Post by Psyphre on 2009-05-19
> **logos34 said:**
> yeah, everything concerning linux hardware support is needlessly obscure...But you can always custom compile your own kernel with the drivers/modules you need for your board and peripherals.

Sounds insanely complex. I struggle as it is with compiling applications, let alone a kernel.

---

### Post by logos34 on 2009-05-19
> **Psyphre said:**
> Sounds insanely complex. I struggle as it is with compiling applications, let alone a kernel.

Believe it or not, it's pretty easy.  (If I can do it, anyone can).  Just need to get all the right hardware modules in during the menuconfig stage, and maybe recompile the graphics driver against the new kernel-headers.  Takes ~30 min average for the machine to crunch the numbers and produce a kernel.

The graphics (nvidia in my case) is the part that's always given me trouble.

---

### Post by Psyphre on 2009-05-20
I was planning to get the P5Q-E, but after looking further, Ive seen a few posts regarding issues (especially dual booting). So now I'm really skeptical and back to square one :(

---

### Post by vincent orange on 2009-05-24
Gigabyte is said to be the most stable and probably the most compatible with Linux.

---

### Post by logos34 on 2009-05-24
> **Psyphre said:**
> I was planning to get the P5Q-E, but after looking further, Ive seen a few posts regarding issues (especially dual booting). So now I'm really skeptical and back to square one :(

The board appears to have a few minor niggles...Apparently [this guy]("http://ubuntuforums.org/showpost.php?p=7226922&postcount=2") is running x64 9.04 Jackalope on asus p5q-e...why not PM him for info?

From what I read some people have problems booting ubuntu unless you enable 'all_generic_ide', or use AHCI Sata mode in the Bios.  If you're dual booting with XP and the latter is already using IDE compatibility mode, you'd have to reinstall XP with the Sata drivers on floppy (or slipstreamed into windows install cd)

hope that helps

---

### Post by Psyphre on 2009-05-24
> **vincent orange said:**
> Gigabyte is said to be the most stable and probably the most compatible with Linux.

Yes that seems to be generally true from what I've seen when looking around. Altho Im totally lost on what to get in terms of a gigabyte motherboard. The ones I wanted dont seem to be sold in the UK, yet all the Asus motherboards are.


> **logos34 said:**
> The board appears to have a few minor niggles...Apparently [this guy]("http://ubuntuforums.org/showpost.php?p=7226922&postcount=2") is running x64 9.04 Jackalope on asus p5q-e...why not PM him for info?

From what I read some people have problems booting ubuntu unless you enable 'all_generic_ide', or use AHCI Sata mode in the Bios.  If you're dual booting with XP and the latter is already using IDE compatibility mode, you'd have to reinstall XP with the Sata drivers on floppy (or slipstreamed into windows install cd)

hope that helps

Thanks, thats a good idea which is why ive been messaging 3-4 people who I've seen this motherboard in their signature. They all seem confident in this motherboard with jaunty, so I think Im going to go with the Asus p5Q-E again.

That being said I dont think many of them dual booted, so the issue you mentioned could be a problem.

I'm a bit confused as to why xp would have an issue if i set it to sata. Surely XP must have sata drivers if the hard drive it's installed on is sata?

---

### Post by logos34 on 2009-05-24
> **Psyphre said:**
> I'm a bit confused as to why xp would have an issue if i set it to sata. Surely XP must have sata drivers if the hard drive it's installed on is sata?

You would think so, but no (hey, that's MS).  You either have to load them from floppy before XP installation (F6 option), or incorporate them into an XP CD (-> nLite).  Otherwise windows will run in what's called ide emulation/compatibility/legacy mode (which is usually fine, as there's no little or no performance difference for the average user--no hot plugging, NCQ, etc.).  BUT if you install ubuntu first in AHCI mode, then windows install cd may not recognize the hdd.  Correction to last post: if you installed ubuntu second and changed the sata mode, you'd have to change it back in the bios before booting windows again (no need to reinstall XP, unless to avoid the hassle).  This normally isn't much of issue, but it can get messy.  Something to think about.

---

### Post by pkjm17 on 2009-05-24
Hey,

I'm putting together a new computer for 9.04 and thinking about this CPU & Motherboard combo. What do you think of this Gigabyte board? It will work on Ubuntu right?

[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.190732](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.190732)

---

### Post by CylnZ on 2009-05-24
if you don't feel like reinstalling xp...

I used this on a clean reinstall a few weeks ago after not bothering with the f6 foolishness.

hXXp://forums.pcper.com/showthread.php?t=444831

---

### Post by Psyphre on 2009-05-25
thank you logos34 and cylnz! Looks like the Asus P5Q-E it is.

Thanks again to everyone who helped. I'll give a review of my progress when I get the board, for anyone else considering this motherboard.

---

### Post by logos34 on 2009-05-25
> **CylnZ said:**
> 
hXXp://forums.pcper.com/showthread.php?t=444831

I've seen that thread before...I guess I'll recommend people try that method first from now one, before going the floppy route...works for some (but not all)

---

### Post by Psyphre on 2009-06-04
Just to update incase anyone see's this thread and also looking for a motherboard.

I bought the Asus P5Q-E, and despite hearing possible issues (for example the sata one and having to reinstall windows) I have NO problems at all. Was completelty plug and play, no settings, no bios, no reinstall.

Brilliant :D

---

### Post by triplemaya on 2012-04-25
In case it is of any help to anyone I am spending my nights trying to get a GA-H61M-S2PV working with Debian. Absolutely no joy with the sound and the ethernet. I have even gone to kernel 3.2 based on suggestions on the net etc etc. I'm looking for something which will just work out of the box if anyone has knowledge of a board which will just work.

---

### Post by MonkeyPaw on 2012-04-25
> **triplemaya said:**
> In case it is of any help to anyone I am spending my nights trying to get a GA-H61M-S2PV working with Debian. Absolutely no joy with the sound and the ethernet. I have even gone to kernel 3.2 based on suggestions on the net etc etc. I'm looking for something which will just work out of the box if anyone has knowledge of a board which will just work.

Seems odd to post this here in this almost 3 year old thread. Why not start a new one?

---

