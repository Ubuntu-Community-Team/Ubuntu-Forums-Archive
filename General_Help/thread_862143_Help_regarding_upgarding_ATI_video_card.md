---
title: "Help regarding upgarding ATI video card"
date: 2008-07-17
forum: General Help
---

### Post by fromgi on 2008-07-17
Can someone please help me select a new Video card which will work out-of-the-box?

I currently have a 32MB ATI Radeon SDR AGP graphics card. [URL="http://assets.gateway.com/s/VIDCARD/ATI/6001675/600167503.shtml"]Here is a link to the specs.
[/URL]  The slot is an AGP 4X/2X/1X.  The card works fine, but I need more to watch HD movies etc.

I'm totally confused, and not sure which card to buy.  I would like to spend around $100 or so.

Any advice is appreciated.

Thanks!

---

### Post by tuxxy on 2008-07-17
I would recommend any recent nVidia card, I recently changed form ATI as the drivers were poor and wouldnt even allow me to run 3D!  I was recommended nVidia over ATI and would now recommend them myself.

[http://ubuntuforums.org/showthread.php?t=860642](http://ubuntuforums.org/showthread.php?t=860642)

If you really want ATI you coud check this for compatibility  

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

---

### Post by fromgi on 2008-07-17
It does not have to be an ATI.  My concern, is that it will work in my current APG 4X/2X/1X slot.

On ebay, I have found [this link]("http://cgi.ebay.com/NEW-Nvidia-GeForce-FX5500-FX-5500-256MB-AGP-Video-Card_W0QQitemZ280246961809QQihZ018QQcategoryZ3762QQssPageNameZWDVWQQrdZ1QQcmdZViewItem") and [this link]("http://cgi.ebay.com/512MB-Nvidia-Geforce-7600GS-7600-GS-AGP-8X-Video-Card_W0QQitemZ280247035946QQihZ018QQcategoryZ3762QQssPageNameZWDVWQQrdZ1QQcmdZViewItem").

I see many as advertised as 4x/8x.  Will these fit into my slot?

Thank you!

---

### Post by stitchmysmile93 on 2008-07-17
Nvidia would be a good choice... if you like projects get an ati...

---

### Post by tuxxy on 2008-07-17
Yes both them cards should run fine out of the box, as there both nVidia which is a wise decision, although I would go with later model myself =p

If your motherboard is AGP then that card should fit fine also.

---

### Post by sloggerkhan on 2008-07-17
I say if it's a desktop, get an ATI. I don't know about finding agp cards, but otherwise their latest driver is as good as the nvidia driver, plus there are functioning open source drivers that even can do 3-D, plus their driver improves nearly every month. I have computers with an ati x700 and an nvidia 8600gt and at this point I regret getting the nvidia card: it plays back video at a slightly lower quality than my x700, though it certainly outperforms it on the games. 

The thing you need to be concerned about is that currently, no linux card really accelerates decode of hi-def streams (mp4, theora, mkv, divx, etc, formats and containers) so even if you have a sweet card that plays back video great, if your cpu is 2ghz+ or so, you'll have trouble decoding 1080p in compressed formats fast enough for smooth playback. (No trouble with 720p or lower, though.)

---

