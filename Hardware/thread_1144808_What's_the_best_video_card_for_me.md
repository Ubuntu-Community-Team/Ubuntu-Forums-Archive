---
title: "What's the best video card for me?"
date: 2009-05-01
forum: Hardware
---

### Post by defaria on 2009-05-01
Here's the situation for me: Bought a new **desktop** (HP) that has an AIT Radeon 3200 HD on the motherboard. This is a 64-bit machine and I'm running Jaunty (9.04). I also have dual monitors. The ATI card supports multiple monitors and generally runs pretty smoothly with the open source drivers but does not do any 3d accelerations. Therefore compiz doesn't work as well as Boxee, Google Earth nor Cool Iris - all things I wish to run. Additionally DVD videos are choppy or just plain messed up when played. I also run Windows Vista in a VMWare session which doesn't support Aero, etc. probably also due to the video driver.

It doesn't look like the ATI driver for my specific video card will be coming out anytime soon and I'm at the point of giving up on this motherboard ATI card and I'm thinking perhaps it'd be best to just buy a better video card and install it instead of continue to fight this problem. Question is: What would be a good video card to buy for my system. I want to use my dual monitor as well as compiz style effects. I want to be able to run Boxee or XBMC as well as Google Earth or Cool Iris. I also want to be able to play DVD videos, etc. IOW I want a video card that performs well. I don't necessarily need a card that handles Crysis or that does heavy gaming as I have a PS3. But if the video card can handle it without breaking the bank then why not?

So what video card do you use that works with 9.04 64-bit and does 3d acceleration without a hitch?

---

### Post by BIOSShadow on 2009-08-09
This the exact question I need. Did you find a answer or did no one respond?

---

### Post by DownTown22 on 2009-08-09
Well, I currently run an [[COLOR="Blue"]_XFX 9600GT_[/COLOR]]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814150397") on my Media Center and it handles all my movies, videos, 3D acceleration and fancy effects (Compiz).  It also has dual DVI ports, so a dual monitor setup should be no problem - I have not tested this out though.

---

### Post by BIOSShadow on 2009-08-09
What do you mean by have not tested? you have not tested the dual monitors? thanks for the help by the way!

---

### Post by swong on 2009-08-09
Nvidia gpus are better supported under Linux.  You should go for GeForce 8 series or higher as it supports hardware video acceleration via VDPAU supported apps (that includes XBMC).

If you have a lesser card (GeForce 7 or lower), then it is still fine for 2D/3D acceleration.  However, when viewing HD content, the decoding is offloaded to the cpu.

Personally I've never had any performance issues running HD content with an Athlon 64 X2 3800 and 7600GT, but better to get GeForce 8 or higher if you can.

I have no idea on the dual monitor setup though, I'm only a single monitor user.

---

### Post by ZaHACKieL on 2009-08-10
> **defaria said:**
> 

It doesn't look like the ATI driver for my specific video card will be coming out anytime soon 

Haven't you tried in the ATI website?

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I see there an ATI Radeon HD 3xxx Series driver for Linux 64. Did you try that and didn't work?

Let me know

---

### Post by BIOSShadow on 2009-08-10
ZaHACKieL, In my case it slowed doem my AMD Athlon64 X2 3.0 GHZ w/ 6 GBS of ram, so much it felt like i had less than 512MB of ram. On top of that the driver install only worked about 50% of the time. but yes i tried them.

---

### Post by DownTown22 on 2009-08-10
> **BIOSShadow said:**
> What do you mean by have not tested? you have not tested the dual monitors? thanks for the help by the way!

Yep, I've never ran a dual monitor setup on this card. But still, I don't see any reason why it wouldn't work.

---

### Post by BIOSShadow on 2009-08-10
thanks DownTown22! Just want to make sure I completely understand.

---

