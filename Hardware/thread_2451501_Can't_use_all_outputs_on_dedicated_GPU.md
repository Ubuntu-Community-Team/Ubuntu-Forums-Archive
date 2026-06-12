---
title: "Can't use all outputs on dedicated GPU"
date: 2020-10-05
forum: Hardware
---

### Post by Daniel_Rosehill on 2020-10-05
Hi,

I have a desktop (Ubuntu + LXDE). The dedicated GPU is the [GeForce® GTX 1050 Ti Windforce OC 4G]("https://www.gigabyte.com/il/Graphics-Card/GV-N105TWF2OC-4GD#kf").

I have been using three outputs with this card for the past several years: 1 monitor is hooked up to the DVI-D output and two to HDMI ports.

However, I bought the card because it was supposed to support four simultaneous outputs. [According to the spec:]("https://www.gigabyte.com/il/Graphics-Card/GV-N105TWF2OC-4GD/sp#sp")

Max outputs is 4

Max total resolution is 7&#8206;680x4320

So I should be able to drive up to 4 displays at 1920 x 1080.

However, when I connected the fourth monitor it would not show up in arandr as an output option. I tested the monitor using my laptop and it works fine. I experienced the same issue (couldn't connect the monitor) while trying to connect it to the HDMI port and the DP.

Is there any way to troubleshoot this? I was using arandr to attempt to get it to connect.

---

### Post by TheFu on 2020-10-08
Which driver is being used?
Does that driver support 4 display output? That's the recommendation I found online.

Have you tried different cables and independently validated the non-working monitor actually works?
Is more power necessary to drive 4 monitors? A less than perfect PSU could be a problem.

Are you using X11 or Wayland? Do those logs show any problems?

---

### Post by Daniel_Rosehill on 2020-10-11
> **TheFu said:**
> 

Have you tried different cables and independently validated the non-working monitor actually works?


Yup, have validated that.

Thanks for the other pieces of diagnostic advice. Will look into the driver and the logs.

---

