---
title: "Nvidia Cards"
date: 2010-01-20
forum: Hardware
---

### Post by logiq on 2010-01-20
Hello everyone.

Does anyone have experience with the latest Nvidia cards on Ubuntu?

I'm considering throwing away my ATI 4870x2 as it has a heating problem and poor driver support, which is driving me nuts.

I was thinking about something like GTX 275, 280 or 285.

Feedback is much appreciated.

---

### Post by peepingtom on 2010-01-20
They are very stable, DirectX programs running under WINE function best using Nvidia drivers. There is a PPA for the latest nvidia drivers here:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

VDPAU is awesome and saves a lot of electricity, you can run it using a $20 video card.

Politically, they suck. But they are very functional.

---

### Post by cascade9 on 2010-01-20
+1 to peepingtom. They might suck politically, but its better than ATI support...I wont even go into matrox and VIA LOL. 

> **logiq said:**
> I'm considering throwing away my ATI 4870x2 as it has a heating problem and poor driver support, which is driving me nuts.

Thrown them my way? :mrgreen:

---

### Post by logiq on 2010-01-20
> **peepingtom said:**
> Politically, they suck. But they are very functional.

Oh, how come?

> **cascade9 said:**
> +1 to peepingtom. They might suck politically, but its better than ATI support...I wont even go into matrox and VIA LOL. 



Thrown them my way? :mrgreen:

Believe me, you'd be better off without it. :roll:

Thanks for your replies!

---

### Post by logiq on 2010-01-20
Guess I'll grab me this one: GeForce GTX 285 2GB SC [http://www.evga.com/products/moreInfo.asp?pn=02G-P3-1186-AR&family=GeForce%20200%20Series%20Family](http://www.evga.com/products/moreInfo.asp?pn=02G-P3-1186-AR&family=GeForce%20200%20Series%20Family)

---

### Post by cascade9 on 2010-01-20
> **logiq said:**
> Oh, how come?

Closed source drivers. Some people dont mind, but there are some who really hate closed source anything. 

I'm not sure if it still happens, but it used to be that if you had nVidia drivers, and looked through the right log file, you would find this msg- 

> "nvidia: module license 'NVIDIA' taints kernel"

> **logiq said:**
> 
Believe me, you'd be better off without it. :roll:

Thanks for your replies!

I _should_ be able to get around the heat problem, but drivers....gah. Unfixable. :|

---

### Post by logiq on 2010-01-20
Oh? I had the same problem in windows tho. Tried to underclock it, but was still high.

Idling now on 81.5c with 30% fanspeed. 

Under load: (While playing Heroes of Newerth)
```

Temperature for thermal controller 0 is 98.000000

Fan speed query: 
Query Index: 0, Speed in percent
Result: Fan Speed: 70%

```
And still sounds like a train..

---

### Post by wolfe on 2010-01-20
I use a gtx 295 on karmic with the newest 195 drivers and in my opinion the pairing of linux and this card works perfectly.  I could not be happier.  Mine is liquid cooled so I can't really say how fan noise and temps are under linux.

---

### Post by wojox on 2010-01-20
I a happy nvidia user. I'm only running a GeForce FX 5300 with the 173.14.20 driver and haven't had any problems.

---

### Post by leehach on 2010-01-20
> **cascade9 said:**
> I'm not sure if it still happens, but it used to be that if you had nVidia drivers, and looked through the right log file, you would find this msg- 





|

I just installed a 7200 GS and I can confirm that the "'NVIDIA' taints kernel" message is still there, which served as a red herring while I was trying to debug installation problems.

Incidentally, thanks for the info about [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa"). I have already installed 190.53 which I downloaded and installed directly, but I much prefer to use package managers. If I add the PPA repository to my Software Sources, will it sync correctly with the already installed package? Or should I uninstall manually and reinstall via the package manager?

---

### Post by logiq on 2010-01-20
> **leehach said:**
> I just installed a 7200 GS and I can confirm that the "'NVIDIA' taints kernel" message is still there, which served as a red herring while I was trying to debug installation problems.

Incidentally, thanks for the info about [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa"). I have already installed 190.53 which I downloaded and installed directly, but I much prefer to use package managers. If I add the PPA repository to my Software Sources, will it sync correctly with the already installed package? Or should I uninstall manually and reinstall via the package manager?

If you do an apt-get update, it will do that automatically - I think.

---

### Post by cascade9 on 2010-01-21
> **logiq said:**
> Oh? I had the same problem in windows tho. Tried to underclock it, but was still high.

Idling now on 81.5c with 30% fanspeed. 

Under load: (While playing Heroes of Newerth)
```

Temperature for thermal controller 0 is 98.000000

Fan speed query: 
Query Index: 0, Speed in percent
Result: Fan Speed: 70%

```And still sounds like a train..

Yeah, well, I wouldnt be trying to underclock it to fix that noise. From the axial spin fans I've used, and ATI coolers in general, I think that it could be solved with either a new heatsink/fan assembly or some degree of hardware hacking. 

For myself, I would try hacking the current shroud around the fan like here- 

[http://www.octeamdenmark.com/forums/extreme-mods/2774-ati-4870x2-full-vmod-cooler-guide.html](http://www.octeamdenmark.com/forums/extreme-mods/2774-ati-4870x2-full-vmod-cooler-guide.html)

I'm not sure that would work well enough for me, and I would guess that I would end up grafting a 120mm fan onto the card. 

BTW, I've seen video cards drop 5-10C at idle when I've pulled the standard heatsink off, removed the cheap thermal paste (that is always on too thick on video cards) and applied a bit of artic silver, then put the standard heatsink/fan back on.

---

### Post by logiq on 2010-01-21
Hm, looks interesting. Looks like a lot of fiddling though. 

But I think I'll go for a Nvidia card anyway, the driver support is a lot better.

Nice article anyway!

---

