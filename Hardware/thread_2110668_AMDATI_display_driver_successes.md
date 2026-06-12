---
title: "AMD/ATI display driver successes"
date: 2013-01-30
forum: Hardware
---

### Post by fizikz on 2013-01-30
The forums are full of issues with AMD/ATI display drivers, but it would be good to hear if some have managed to get their graphics cards working well, including 3D acceleration and other features such as multi-monitor support, etc. 

So, if you have an AMD/ATI graphics card and have a working setup, please post so that others will know there is hope. I'm looking to buy a laptop with a 7970M, with no Enduro (integrated graphics), and would be particularly interested to know if others have had success with the drivers and functionality. 

Thanks!

---

### Post by Mark Phelps on 2013-01-31
No replies in 19 hours -- not good.

I know some folks are using AMD restricted drivers with success, I'm just not one of them because my video chipset got dropped by AMD from their support last summer and I'm relegated to the open source drivers now.

You might do better if you ask about the specific laptop model you want to buy.  Laptop video chipsets tend to be customized and the same model chipset in a video card may not work exactly like that customized chipset on a laptop motherboard.

Plus, Video is not the only concern with a new laptop.  I'd also ask about Networking (wired and wireless) and temperature control (as some chipsets aren't supported well in Linux and tend to overheat).

---

### Post by fizikz on 2013-01-31
Thanks for your comments, Mark.

I'm considering the Sager NP370 / Clevo P370EM. It seems most of its components work in linux and the biggest variable is the graphics card. I've read that the open source radeon drivers do work on it. 

How useable do you find the open source radeon drivers? 

I'm looking to use the proprietary drivers, at least initially. I think it's bad enough to have support dropped for an older chipset, but if a new chipset doesn't work well under linux, I think that is a bitter pill to swallow for a new purchase.

---

### Post by Mark Phelps on 2013-02-01
> **fizikz said:**
> How useable do you find the open source radeon drivers? 
Thankfully (since I have no real choice!), they are quite good.  When I started using ATI video hardware years ago in Ubuntu, the only way to get high resolutions or multi-monitor support was to use the restricted drivers -- and installing them was such a hassle that, like so many other, I resorted to using the Envy utility.

But, since 12.x, I've found the open-source drivers give me both full resolution (1920x1280) and multi-monitor support.  Since I'm not doing any Gaming or GPU overclocking, these suffice for me.

> I'm looking to use the proprietary drivers, at least initially. I would suggest you at least try the open-source to see if they work for you. 

> I think it's bad enough to have support dropped for an older chipset, but if a new chipset doesn't work well under linux, I think that is a bitter pill to swallow for a new purchase.
Agree --  the chipset I use is STILL being sold in the marketplace and AMD has already dropped restricted driver support for it.

---

### Post by fizikz on 2013-02-01
> **Mark Phelps said:**
> Agree --  the chipset I use is STILL being sold in the marketplace and AMD has already dropped restricted driver support for it.

That's unbelieveable..Just a thought, what about using older versions of the Catalyst drivers that supported your chipset?

---

### Post by Bashing-om on 2013-02-01
Guys;

I am running an AMD (Athelon x2) setup with an ATI graphics card (RV515 - Radeon X1300) Old card using the open source Radeon driver. Straight out of the box not a problem one !
[INDENT][INDENT]what can I say 
[/INDENT][/INDENT]

---

### Post by fizikz on 2013-02-01
> **Bashing-om said:**
> Guys;

I am running an AMD (Athelon x2) setup with an ATI graphics card (RV515 - Radeon X1300) Old card using the open source nouveau driver. Straight out of the box not a problem one !

[INDENT][INDENT]what can I say 
[/INDENT][/INDENT]

Glad things are working for you, but to my knowledge, the nouveau drivers are the reverse-engineered open source drivers for NVIDIA graphics cards. The open source drivers for ATI graphics cards is called radeon.

---

### Post by Yellow Pasque on 2013-02-02
I wouldn't use open-source radeon drivers on a laptop. Their power consumption can be markedly higher than the proprietary driver. Basically, I wouldn't buy a laptop with an AMD GPU until they get power management straightened out.

Intel HD3000/4000 graphics are the way to go for non-hardcore gamers.

---

### Post by Bashing-om on 2013-02-02
Radeon driver in use and post edited to reflect such. Thanks for pointing out my error.

---

### Post by Mark Phelps on 2013-02-03
> **fizikz said:**
> That's unbelieveable..Just a thought, what about using older versions of the Catalyst drivers that supported your chipset?

Older version of the Catalyst drivers won't work anymore with the introduction of Ubuntu 12.10.  It uses a newer X-server version that these older drivers can't use.

---

