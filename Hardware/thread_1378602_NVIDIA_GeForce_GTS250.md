---
title: "NVIDIA GeForce GTS250"
date: 2010-01-11
forum: Hardware
---

### Post by marcozs on 2010-01-11
Hey everyone,

I am considering to buy a new graphic card and I thought about the MSI NVIDIA GeForce GTS250 OC.

Before buying it I'd like to be sure it will be fully compatible with Ubuntu 9.10, has anyone tried it out?

I read I have to install the nvidia 190.53 drivers (or 195?), is it safe to do it from [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/) ?

Waiting an answer before the purchase...
Thanks in advance!

---

### Post by buntunub on 2010-01-12
Yea, I have this model using those drivers. Works like a champ. I compile my drivers though and reinstall after each kernel update. I have a dual DVI monitor setup this way on Kubuntu and its fantastic.

---

### Post by buntunub on 2010-01-12
Here is what my Kubuntu Karmic 64 bit desktop looks like.

---

### Post by marcozs on 2010-01-12
> **buntunub said:**
> I compile my drivers though and reinstall after each kernel update.

I've also got karmic 64bit with nvidia 8600gts but I wanted to upgrade to GTS250... do you think I will have problems if I don't compile them and use the ppa version of the drivers?

---

### Post by barnex on 2010-01-12
I've just ordered a (really nice) gtx295. I'll let you know if it works when it arrives, but I assume nvidia cards are usually quite well supported.

---

### Post by marcozs on 2010-01-12
> **barnex said:**
> I've just ordered a (really nice) gtx295. I'll let you know if it works when it arrives, but I assume nvidia cards are usually quite well supported.

wow nice one! A bit too expensive for me, I think I will go for the GTS250...

---

### Post by marcozs on 2010-01-12
> **buntunub said:**
> Here is what my Kubuntu Karmic 64 bit desktop looks like.

What dock are you using? gnome-do docky? or cairo-dock?

---

### Post by coskierken on 2010-01-12
Both Cairo Dock and AWN work fine with the GTS250.  I have the OC/1Gig version of this card.  The ppa work fine with them.  Watch the fan speeds on the card.  If you play any games or serious 3d work, make sure the the fan speeds are 75% or better or it may overheat and lock up.  I actually got the Zalman all copper/tube cooler and chipset heatsinks for this model.  It lowers temps quite a bit, thus more stable at higher usage.  Hope this helps.

---

### Post by cascade9 on 2010-01-12
Just in case you dont know....the GTS250 is a 9800GT, which is a 8800GT. Theers been die-shinking and some updating, but the basic chip hasnt changed in a long time. 

If your gaming, the GTX260 is a better choice, if you can afford the few extra dollars it costs. If your not gaming....in most cases the 8800/9800/250 is overkill.

---

### Post by buntunub on 2010-01-12
Im not using a docker. That is the KDE4 panel. Those are standard Kwin effects and the rest is all Plasma.

As far as the drivers, you can try PPA's and may have some success. I tried them and they failed on kernel upgrades and I still had a little bit of weird artefacting with them. Its just easier for me to get the driver from Nvidia and reinstall it each time. Its a self installing executable that does everything automatically:

CTRL+ALT+F1, or boot into safe mode, then

```
sudo (omit sudo if in safe mode) sh NVIDIA..... .run
```


reboot

done.

---

### Post by buntunub on 2010-01-12
> **cascade9 said:**
> Just in case you dont know....the GTS250 is a 9800GT, which is a 8800GT. Theers been die-shinking and some updating, but the basic chip hasnt changed in a long time. 

If your gaming, the GTX260 is a better choice, if you can afford the few extra dollars it costs. If your not gaming....in most cases the 8800/9800/250 is overkill.

This old review posted [here]("http://techreport.com/articles.x/16504") indicates that you are correct to a point.

> All of which leads us to the inevitable price and performance comparison, and here, the GeForce GTS 250 offers a reasonably compelling proposition. This card replicates the functionality of the GeForce 9800 GTX+ in a smaller physical size, with substantially less power draw, at a lower cost. I like the move to 1GB of RAM, if only for the sake of future-proofing and keeping the door open to an SLI upgrade that scales well. In the majority of our tests, the GeForce GTS 250 proved faster than the Radeon HD 4850 1GB, if only slightly so. If the Radeon HD 4850 1GB were to stay at current prices, the GTS 250 would be the clear value leader in this segment. 

And [here]("http://www.pcper.com/article.php?aid=674&type=expert&pid=9")

> Regardless of the politics involved, the GeForce GTS 250 1GB card does do one thing: decrease the price of great gaming GPU solutions from both NVIDIA and AMD for the consumer.  Fan boys on either side will surely complain about how the other group is doing it, but it's a win for all of us.  You can now essentially buy a graphics card that will play most of today's recent PC titles at resolutions of 1600x1200 and above with top IQ settings for under $150, regardless of which GPU vendor your choose.  How's that for a way to help get out of the funk of winter? 

With prices now hovering around $130 for the 1GB model (which is what I have), its a good deal for this type of card. The 4850 may be the better option for gamers as both of these professional grade reviews have determined, but ATi + Linux = terribad support and worlds of headaches after every xorg and sometimes kernel upgrades and sometimes even regular updates, no thanks! My performance levels with Nvidia have always been spectacular in both Windows and Linux. 

The performance of this card on Bioshock and Dragonage on maximum settings across the board has been flawless with great fps and hours of gameplay nonstop. I cant do that with my 8800GT OC (512G). The 9800 cant do that either. The GTS250 does it with ease and at a price point that blows away any slight performance gains you get from the GTX's (which you will only see in Windows - you wont see any of it in Linux, btw). While it may be the political thing to think that the most expensive graphics option is the best, it is usually not the case. In the long run, your better off buying a slightly older card based on proven technology dynamics such as this one (G92 chipset) for a much lower price.

---

### Post by marcozs on 2010-01-12
> **coskierken said:**
> If you play any games or serious 3d work, make sure the the fan speeds are 75% or better or it may overheat and lock up.

Do I have to set the fan speed manually?
I thought it would autoadjust... 
Anyway I will mostly play World of Warcraft

> **coskierken said:**
> I actually got the Zalman all copper/tube cooler and chipset heatsinks for this model.  It lowers temps quite a bit, thus more stable at higher usage.  Hope this helps.

I was thinking to get either the 512Mb:
[http://www.eprice.it/images/Prodotti/plus/n2402018.jpg](http://www.eprice.it/images/Prodotti/plus/n2402018.jpg)

Or this one, 1Gb version:
[http://www.eprice.it/images/Prodotti/plus/n2329107.jpg](http://www.eprice.it/images/Prodotti/plus/n2329107.jpg)

Not sure if the 1gb is worth the 30 euros more...

---

### Post by marcozs on 2010-01-12
> **buntunub said:**
> The 4850 may be the better option for gamers as both of these professional grade reviews have determined, but ATi + Linux = terribad support and worlds of headaches after every xorg and sometimes kernel upgrades... 

Yeah that's the same I thought, I have had nvidia since the very beginning of 3d graphic cards, and never a problem... especially on linux the drivers are much better supported, plus I head they want to make the driver even more open...

> **buntunub said:**
> The GTS250 does it with ease and at a price point that blows away any slight performance gains you get from the GTX's (which you will only see in Windows - you wont see any of it in Linux, btw).

Yes you need directx10 to gain performances with the GTX chipsets, isn't it?

---

### Post by marcozs on 2010-01-12
> **cascade9 said:**
> If your gaming, the GTX260 is a better choice, if you can afford the few extra dollars it costs. If your not gaming....in most cases the 8800/9800/250 is overkill.

well my 8600gts has done pretty well until now, I am not playing very tough 3d games, just World of Warcraft and a couple of others, not really into FPS for example. I am changing the graphic card just cause I need another pci-e card for my parents'desktop, so I thought to get a little upgrade and give them mine instead of buying a low price one... ;)

---

### Post by marcozs on 2010-01-12
By the way I had a look at the power consumption graph:
[IMG]http://www.pcper.com/images/reviews/674/power.jpg[/IMG]

My Corsair 550VXEU 550Watt shouldn't have any problem, right?
It's 33A on the 12V output...

---

### Post by cascade9 on 2010-01-12
> **buntunub said:**
> The performance of this card on Bioshock and Dragonage on maximum settings across the board has been flawless with great fps and hours of gameplay nonstop. I cant do that with my 8800GT OC (512G). The 9800 cant do that either. The GTS250 does it with ease and at a price point that blows away any slight performance gains you get from the GTX's 

I agree on ATI..I really wish they would get things together for linux, I'm hoping they do soon. 

I'm suprised at the difference between the 8800/9800/250 in your experience, but sometimes these things happen. 

As for price difference, its not as much as you might guess. Using the site that marcozs posted

GTS250 1GB- 125 eruo- (130 for the MSI OC version)
[http://www.eprice.it/Schede-Video-GIGABYTE/s-2335669](http://www.eprice.it/Schede-Video-GIGABYTE/s-2335669)

GTX260 (898MB)- 150 eruo. 
[http://www.eprice.it/Schede-Video-ASUS/s-2339839](http://www.eprice.it/Schede-Video-ASUS/s-2339839)

> **buntunub said:**
> (which you will only see in Windows - you wont see any of it in Linux, btw). While it may be the political thing to think that the most expensive graphics option is the best, it is usually not the case. In the long run, your better off buying a slightly older card based on proven technology dynamics such as this one (G92 chipset) for a much lower price.

Now, this I have trouble believing, to be honest. But this is the hardware capabilities (and I'm not sure if the card I posted before was a 'original' GTX260 or the '216 core' version, posted figures are '216 core'-

GTS 250- 128:64:16 (Unified Shaders:Texture Mapping:Render Output) Bandwidth- 70.4GB/sec. 
GTX 260- 216:72:28 (Unified Shaders:Texture Mapping:Render Output) Bandwidth- 111.9GB/sec.

Yeah, the core, shaders, and memory speeds are lower on the GTX260. But from everything I know, I would think that in some games the GTS250 would be faster, or at least be as fast (more older games) and the GTX260 would be faster on other games (more newer games). 

You would have to see something from the extra shaders, texture mapping and render output in games that used them. The bandwidth alone would give the GTX260 an edge on some things linux or windows.  I'd like to see some linux benchmarking on GTS250 vs GTX260 but I couldnt find any. 

BTW, dont think I'm that 'down' on the GTS250. Its a nice card, I wouldn't mind running one myself..it would be an upgrade from my current 8600GT. I'm upgrading my CPU 1st though (from 4800+ to, ohh, probably a X4 955), since I use CPU power more than video card power. I'm not much of a gamer anymore

True, you do have a point about the general idea that higher cost automatically gives better performance. Its a myth in some cases. 

> **marcozs said:**
> My Corsair 550VXEU 550Watt shouldn't have any problem, right?
It's 33A on the 12V output...

It will do it, easy :)

---

### Post by marcozs on 2010-01-12
> **cascade9 said:**
> 
GTS250 1GB- 125 eruo- (130 for the MSI OC version)

I was actually going for the MSI OC version...

> **cascade9 said:**
> GTS 250- 128:64:16 (Unified Shaders:Texture Mapping:Render Output) Bandwidth- 70.4GB/sec. 
GTX 260- 216:72:28 (Unified Shaders:Texture Mapping:Render Output) Bandwidth- 111.9GB/sec.

Here a very nice website with comparison between GTX260 and GTS250:
[http://www.tomshardware.com/reviews/geforce-gtx-260,2286.html](http://www.tomshardware.com/reviews/geforce-gtx-260,2286.html)

Now I am actually considering to wait the price to drop and get this MSI GTX260 with some nice 1.8Gb DDR3:
[http://www.tomshardware.com/reviews/geforce-gtx-260,2286-10.html](http://www.tomshardware.com/reviews/geforce-gtx-260,2286-10.html)

Ok... maybe joking :) right now it's double price of GTS250...

> **cascade9 said:**
> I'm upgrading my CPU 1st though (from 4800+ to, ohh, probably a X4 955), since I use CPU power more than video card power. I'm not much of a gamer anymore

That's exactly what I did, upgraded to Phenom X4 955 which is making my Karmic 64bit run so smooth!

---

### Post by buntunub on 2010-01-13
Well, ultimately were all at the mercy of the hardware vendors. We have ATi = crap linux support, INTEL - yea right. Great cards for average (non Gamer types), excellent (up until Karmic) support in Linux. Then we have NVIDIA - Outstanding Windows support, good Linux support, but closed source (YUCK!!). So what we have is lose, lose, and lose. Take your pick of the best of 3 bad choices, imo. Thats what I think anyway, but since I do game I have to choose a card that fits all my needs at a good price point with stable, proven hardware. That is the GTS250 for now. Before that it was the 8800 (an absolutely fabulous card). If I never gamed, then I would choose INTEL.

---

### Post by marcozs on 2010-01-13
> **buntunub said:**
> Then we have NVIDIA - Outstanding Windows support, good Linux support, but closed source (YUCK!!). 

I believe linux support is more than good: I think if there were more games developed natively for linux the 3D performances would be very close to windows ones with the actual nvidia drivers...
I agree on the fact that the drivers are closed but there might be an opening on that point... Petition here:
[http://www.petitiononline.com/nvfoss/petition.html](http://www.petitiononline.com/nvfoss/petition.html)

> **buntunub said:**
> I do game I have to choose a card that fits all my needs at a good price point with stable, proven hardware. That is the GTS250 for now. Before that it was the 8800 (an absolutely fabulous card). If I never gamed, then I would choose INTEL.

I agree on this, but since AMD bought ATI maybe there will be some news from Intel on high-end graphic cards as well and not only notebook/netbook ones...

---

### Post by barnex on 2010-01-13
> **marcozs said:**
> wow nice one! A bit too expensive for me, I think I will go for the GTS250...

Well, that 295 is only for CUDA simulations, there will be no gaming on it, unfortunately...

---

### Post by Jive Turkey on 2010-01-13
I have a GTS250 1GB from XFX and it worked great with the the restricted driver and later with the 195.xx driver.  Very pleased and conky can read the temp on the card without any additional scripts.

I have read that the 250's are really the same hardware as the 8800's though.

---

### Post by marcozs on 2010-01-13
> **barnex said:**
> Well, that 295 is only for CUDA simulations, there will be no gaming on it, unfortunately...

No gaming for GTX295? On gaming one GTX295 performs close (just about 10% below) to 2 (two!) GTX275 in SLI... and a lot less power consumption...

[IMG]http://media.bestofmicro.com/6/T/210197/original/image024.png[/IMG]

---

### Post by cascade9 on 2010-01-13
> **marcozs said:**
> No gaming for GTX295? On gaming one GTX295 performs close (just about 10% below) to 2 (two!) GTX275 in SLI... and a lot less power consumption...

Not that suprising that 2xGTX275s is faster than a GTX295. The 295 is pretty much 2x275s (SLI on a signle card) @ 260 speeds. Odd about the power consumption though. 

I'd probably still take a GTX295 over 275s in SLI. No need to sod around with SLI connectors, etc.....ohh, and it will run on any motherboard with PCI-E. SLI wont work on any ATI chipset (my current setup) and the only common Intel chipset with SLI support is the new x58 for i7.  

Not that I'm in the market for that sort of video power though.

---

