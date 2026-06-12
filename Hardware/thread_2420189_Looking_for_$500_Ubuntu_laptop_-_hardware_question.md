---
title: "Looking for $500 Ubuntu laptop - hardware questions."
date: 2019-05-31
forum: Hardware
---

### Post by mfmelhus on 2019-05-31
Want a Ubuntu (only, no dual boot) laptop to get better at using linux, perform general tasks, connect to another Linux server, etc.  Considering the following:

HP Pavilon 15Z - On special for memorial day (ends Saturday, but same pricing around fourth of July):
AMD Ryzen 5 processor[SIZE=4][FONT=trebuchet ms] [FONT=verdana][COLOR=#000000]2500U Quad-Core (2 GHz)[/COLOR][/FONT][/FONT][/SIZE]
AMD Radeon Vega 8 graphics
16 GB DDR4 memory
256 GB  [COLOR=#000000][FONT=HPSimplifiedLight]PCIe® NVMe™ M.2 SSD
[/FONT][/COLOR]$519 with free shipping.
[https://store.hp.com/us/en/pdp/hp-pavilion-laptop-15z-best-value-5gr40av-1?jumpid=ma_memorial-day-sale_product-tile_laptops_6_5gr40av-1_hp-pavilion-laptop--](https://store.hp.com/us/en/pdp/hp-pavilion-laptop-15z-best-value-5gr40av-1?jumpid=ma_memorial-day-sale_product-tile_laptops_6_5gr40av-1_hp-pavilion-laptop--)

Lenovo IdeaPad 340S
Numerous models, between $400 and $500.
Both Intel and AMD processors.

Anyone with experience with either of these?  How hard is it to get everything working right under Ubuntu?  Good instructions online for finding appropriate drivers and such?  I don't want the install to be so painful that I give up and return the computer (and yes, I plan on trying it first from the boot thumb drive).

Or, if there's something in my price range that's better than either of these, would like to hear about it.  Want full HD, a decent quality keyboard with a number pad, and fairly light weight.

Thanks in advance.

Regards,
Martin


Any advice appreciated.

---

### Post by SeijiSensei on 2019-06-01
Since both machines will come with Windows installed, you'll need to make some changes to the hard drive.  HPs (and maybe Lenovo's as well) come with all four primary partitions on the hard drive in use making it impossible to install Ubutnu anywhere.  If you don't care about keeping Windows, you can choose the "use the whole disk" option during installation which will blast those partitions, and thus Windows, away. 

I've got both an HP and a Lenovo with Kubuntu 19.04 running on each.  I'd lean toward the Lenovo myself, since support for AMD graphics has been pretty spotty over the years. (I only use NVIDIA cards or just rely on the built-in Intel video which works fine these days.)

---

### Post by mfmelhus on 2019-06-01
Thanks for the info.

I'm still quite uncertain as to whether to go with AMD or Intel - some reports here and elsewhere have mentioned that AMD has been involved in Linux development lately, and have much better support for Ubuntu and other linux distros.  Your experience says the opposite.

The HP is also available in an Intel model that loses the touch screen (put it back for $40, is that a big deal or not useful?), reduced the memory from 16 GB to 4GB (easy fix, though), and has a core i5 8250 with integrated Intel video, which costs $20 less (or $20 more with touch).

The Lenovo Intel model has backlit keyboard (not a big deal, $20-$30 upgrade on the HP), but touch costs another $80 on the intel machine, and almost $200 on the AMD machine.  Both have 8 GB RAM, 4 onboard +4 in a slot, so can only be upgraded to 12, not 16.

What matters the most?  How easy is the install on each?  Don't want to buy a brick.

Martin

---

### Post by SeijiSensei on 2019-06-01
I never use touch on computers, just smartphones. I haven't ever missed it.

None of my machines have more than 8 GB of RAM. Unless you're intending to run a lot of virtual machines via VirtualBox or KVM, I'd say 8-12 is more than enough.  If you create large illustrations or edit large graphic objects, more memory might be helpful.  But I can open a 4000x3000 pixel image in GIMP and edit it without problems.

I don't know about AMD's recent efforts, but NVIDIA devices have been rock-solid in Linux for many years.

Have you ever installed Linux from scratch before? You shouldn't have any problems on those machines. Even touch seems relatively well-supported these days: [https://www.maketecheasier.com/best-linux-desktop-touch-enabled-monitor/](https://www.maketecheasier.com/best-linux-desktop-touch-enabled-monitor/)

---

### Post by CatKiller on 2019-06-01
I've happily used nvidia cards on the desktop for years, but I wouldn't use an nvidia chip in a laptop. Their *doing their own thing* approach for the proprietary driver makes it a pain to use both the nvidia chip and the integrated graphics. If you only use the nvidia one, your battery life suffers; if you only use the integrated, you didn't need to pay for the nvidia. 

Just using integrated graphics from Intel or AMD will be less trouble than mixing them up with nvidia ones. AMD if you want more performance and you're happy using very new software. Intel if you don't need as much performance, or you're happier with LTS software. Support for the AMD APUs didn't make it into 18.04, and it's still a work-in-progress.

---

### Post by mfmelhus on 2019-06-01
Catkiller wrote:
[COLOR=#000000]"Support for the AMD APUs didn't make it into 18.04, and it's still a work-in-progress."[/COLOR]

[COLOR=#000000]Thanks.  That's exactly the data I'm looking for.  Has me leaning strongly towards Intel with their built in graphics.  I have no desire to run bleeding edge - LTS is a much happier place for me to live.  I have enough complications in the research I'm doing (physics of granular materials), and I don't need OS issues on top of that.

SeijiSensei wrote:
"[/COLOR][COLOR=#000000]None of my machines have more than 8 GB of RAM. Unless you're intending to run a lot of virtual machines via VirtualBox or KVM, ...."[/COLOR]

[COLOR=#000000]Good to know.  The Lenovo Intel version or the HP Intel version sound like where I want to put my money, based on this info.  Thanks again, both of you.

Martin

[/COLOR]

---

### Post by CatKiller on 2019-06-01
> **mfmelhus said:**
> Thanks.  That's exactly the data I'm looking for.  Has me leaning strongly towards Intel with their built in graphics.  I have no desire to run bleeding edge - LTS is a much happier place for me to live.

As I understand it (I have Nvidia on my desktop and Intel in my laptop and HTPC, so it's only what I've picked up elsewhere) the AMD stuff is pretty solid in 19.04, and it should all be squared away for the next LTS in 2020. It was just awkward timing for them with the way their release timetable and the schedules for Ubuntu failed to line up properly. Intel have much more resources available to get driver support integrated before they release their hardware.

---

### Post by mfmelhus on 2019-06-01
Cool, thanks.  The computer I'm doing research simulations runs on an AMD high end desktop processor (or it was when I bought it) as well as a top shelf motherboard, and a Nvidia 980 Ti that I do simulations on in CUDA.  It runs Ubuntu just fine (well, better than fine, it's still blazing fast, and the simulations only depend on the speed of the graphics card. It's the laptop world that I'm more lost in.  Thought about getting something with Nvidia graphics so I could do some simple tests on it, but that would raise the price and weight of the laptop, and that's not what I want it for.

Again, appreciate all the help.  Looks like the best choice is the Lenovo S340 with SSD and the FHD screen, i5 and the Intel UHD 620 integrated graphics card.  Should come in under $500, much less if the discount program at my wife's work comes through (perhaps 30% off).

Regards,
Martin

---

