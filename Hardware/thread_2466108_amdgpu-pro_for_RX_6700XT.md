---
title: "amdgpu-pro for RX 6700XT?"
date: 2021-08-19
forum: Hardware
---

### Post by DuckHook on 2021-08-19
I'm in a bit of a pickle and would value the advice of the good people here:

I've recently upgraded my failing 9-yr old video card to an AMD RX 6700 XT. Though pricey, I expect it to last me close to another decade. My problem is that, in order to get this new toy to work, I've had to install the 20.04 HWE stack for it to recognize the card and run the AMDGPU driver.

The crazy thing is that this card now runs some Steam games more slowly than my old card. Old card was a 7950 that could not even run amdgpu because it wasn't supported. It could only run the old and tired radeon driver, yet that old card/radeon driver combo ran games a lot faster than the new card/amdgpu driver setup.

I've downloaded the amdgpu package from AMD's site and am considering installing amdgpu-pro, but have not installed it yet. I figured that I would ask the advice of knowledgeable forum members before taking that leap. Though I have nothing against proprietary blobs in principle, they have led to instabilities and gnashing of teeth for me in the past. Since installing such drivers is easy but backing them out is hard, I want to make sure that I'm not buying myself a mess of trouble before proceeding.

All advice and comments appreciated.

---

### Post by DuckHook on 2021-08-20
UPDATE

Since I have another partition with another Ubuntu install, I decided to try amdgpu-pro on that other partition and everything works very nicely so far (though it's still early goings). I will experiment a bit further with that one before taking the leap on my main install.

---

### Post by DuckHook on 2021-08-20
Further update:

Running glxgears shows that the newest amdgpu-pro driver works four times as fast on my experimental install as the older pure FOSS driver bundled with my main install. Aside from the very real added incentive to upgrade the driver, why would there be such a big performance difference? I thought they were both based on the same FOSS engine.

---

### Post by Yellow Pasque on 2021-08-20
I would have tried the oibaf PPA for such a new card.

---

### Post by DuckHook on 2021-08-20
> **Yellow Pasque said:**
> I would have tried the oibaf PPA for such a new card.
Thanks YP. I did already take the plunge and added oibaf's PPA (against my usual overcaution), but upgrading the driver brought no joy. Same performance as before, whereas the experimental Ubuntu instance running the pro driver is fast and furious.

I also acknowledge that this card purchase was uncharacteristically reckless for me. But the box said Linux compatible and preliminary research indicated Ubuntu support, though I later discovered that this meant using their driver download.

Still fooling around with it and trying to tease out the reasons for the large performance delta.

---

### Post by Bashing-om on 2021-08-20
DuckHook; Dunno

But will Michael Larabel's benchmarks be of any help to you: [https://www.phoronix.com/scan.php?page=article&item=radeon-rx6000-vulkan&num=1](https://www.phoronix.com/scan.php?page=article&item=radeon-rx6000-vulkan&num=1)

[INDENT]something I ran across
[/INDENT]

---

### Post by DuckHook on 2021-08-20
Thanks Bashing…

I don't play high resource games like fast shooters, so the absolute bleeding edge is not needed. However, there's enough going on in Steam+ Civ 5 to bring a subpar video system either to its knees or to an outright crash. My old video card would play the game reasonably well, but then crash and burn without any warning, taking the whole system down with it. This was happening with increasing frequency and was why I changed it. The new card no longer crashes the whole system, but takes a full 30 seconds to paint the tiles in a 1920x1080 game window. There is no way that such a beast of a GPU should be taking that long, so I suspect subpar drivers. Haven't tried the Steam + Civ 5 combo in the alternate install yet. That's tonight's task, which should give me the feedback needed to see exactly how much better the pro driver is.

The benchmarks are sort of academic at this point, since the card is not returnable. This was made clear by the retailer from the outset (GPUs are in such high demand that they will not accept returns). I did say it was a rather reckless purchase for me… :redface:

Thanks for the link though!

---

### Post by linuux on 2021-08-21
Hello, I am reluctantly interrupting (because I don't know if my questions/comments will help or be an annoyance) but wasn't the rx 6700 xt released in March?

It's still not working with the FOSS amdgpu driver?  Don't games/Steam work okay with FOSS amdgpu?  

Edit:  Oh, it works but is really slow (I assume, unacceptably so)?

I am just curious what happens if you boot up a live iso or 'brand new' fresh install of 21.04 with it, preferably with 'up-to-date' Mesa (plus recent kernel, 5.11 at least or newer) and maybe Vulcan?  It works generally but once you try to run games or various software, it doesn't work up to par (I hear OpenCL isn't too great)?

I hope you know what I am talking about because I barely do. :)   I know that Phoronix gets cited but these are 'ootb' configurations - just doing benchmarks - that's one thing, it's another to get a card working on your own, personal system - with your own configuration - right?

I am curious how the 6700 xt experience compares to running, a 3060 ti, for e.g. - as I am debating these two cards when/if I can invest in a new build.

I might 'downgrade' to 1660S/2060 or Rx 580/590/5600 xt depending how prices are and availability is when I am in the market to buy.  

Maybe Nvidia will work well with XWayland by then :-{  (Just a bit of humor there?).

---

### Post by mastablasta on 2021-08-23
what is current kernel in 20.04 HWE?

something with that particular card. my kid has Ryzen 5 3500U which has Vega on it and Steam stuff runs really well. i would say just install the pro driver. maybe by 2022 LTS edition everything will work out of the box on the open source driver.

i recently found out the other kids PC generates plenty of heat. Not sure if it's the older Ryzen 7 or the GTX, but i suspect the GPU. so i am thinking i need to get something that is reasonably fast and doesn't generate so much heat playing Enemy Territory. i plan to upgrade next year as current prices are just crazy + i need to buy new monitor as well (currently on 17 year old on SVGA 4:3).

crazy that there are no descent cards in below 200 EUR price range.

---

### Post by linuux on 2021-08-24
> **mastablasta said:**
> what is current kernel in 20.04 HWE?

something with that particular card. my kid has Ryzen 5 3500U which has Vega on it and Steam stuff runs really well. i would say just install the pro driver. maybe by 2022 LTS edition everything will work out of the box on the open source driver.

i recently found out the other kids PC generates plenty of heat. Not sure if it's the older Ryzen 7 or the GTX, but i suspect the GPU. so i am thinking i need to get something that is reasonably fast and doesn't generate so much heat playing Enemy Territory. i plan to upgrade next year as current prices are just crazy + i need to buy new monitor as well (currently on 17 year old on SVGA 4:3).

crazy that there are no descent cards in below 200 EUR price range.The heat issue might just be that it's a laptop - the Vega graphics is one thing but if the laptop cooling (i.e. fan/vent) design is subpar, there might be a lot of heat when gaming or stressing the chip.  

The kernel in 20.04 in HWE is probably 5.11*?  

If I was having issues afterwards, I would probably upgrade the kernel to at least 5.13.  I have discovered a number of user reports on issues with RX 6700 XT/RX 6600 xt issues.  Dunno if that extends to the 6800 and 6900 series.

---

### Post by DuckHook on 2021-08-31
Apologies for the late reply. I'm marking this thread "solved" because I have now tested the vendor downloaded amdgpupro for more than a week and can report that it is stable and ***fast***, so I'm going to stick with it. In contrast, the latest drivers I could find through "normal" channels (even the oibaf PPA) did not run well on this card. Though stable, they left so much performance on the table that my old HD7950 was superior.

My only problem is minor&#8212;well, perhaps not so minor&#8212;playing Civ 5 on Steam leads to segfaults of such severity that they instantly reboot the whole system without warning. But that's confined to Civ 5, is a somewhat known problem and doesn't belong on this thread in any case. I'll start a new thread in *games* if I think it's important enough.

Thanks to all for your help and your input.

---

### Post by Bashing-om on 2021-08-31
DuckHook;

Pleased to see this report, that you did the leg work - noted :D

Bummer that it is the OEM driver that performs the better :(


[INDENT]not what I may wish

[INDENT][INDENT]but what is, is
[/INDENT][/INDENT][/INDENT]

---

### Post by DuckHook on 2021-09-01
> **Bashing-om said:**
> …Bummer that it is the OEM driver that performs the better :( …
Mostly my own fault. I knew it was a spanking new card and, of all people, should have suspected that FOSS driver support would be lagging, but getting ***any*** sort of card from the local shop these days is an ordeal, so I just made the jump somewhat blindly. I'm sure that the next iteration of LTS in a few months time will have it straightened out.

---

