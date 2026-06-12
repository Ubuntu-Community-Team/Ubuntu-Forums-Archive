---
title: "6600GT driver use."
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by cobolt01 on 2007-10-14
I'm starting to get very irritated with configuring the video drivers for my Ubuntu install. First I was using the onboard X1250 and after struggling for a few days and realising that there will never be 3D accelleration, I installed the 6600GT that I have. I realised that I'd have to change the driver I was using. So when I booted up, X had it's little fit and I reconfigured it to use nv drivers. That didn't work. So I installed the nvidia-glx drivers and used config enable to change the xorg.conf file to the nvidia settings. X still won't start. I'm really getting sick of fiddling with this. Can't there just be a driver that I download and install? There are also about 10 other video drivers installed (for other chipsets), but they all seem to be generics because I didnt install most of them. It's looking like a Windows XP solution for me, because at least there is driver support. Although I don't want to have all the other hasstles involved.
I have some ATI drivers installed.
the Nvidia-glx driver installed and enables.

I am almost an expert on this by now, so I don't need the commands copied. Just please, please, please tell me what I should do from here to get the 6600GT at least working with X and Gnome. Thanks in advance.

---

### Post by PmDematagoda on 2007-10-14
Since you are now using a separate VGA card as opposed to your integrated one and as the X-server may still be using the integrated VGA's address, there would be a problem, so the main thing you will have to do, is change the address specified in the xorg.conf file to the one that is used by your VGA card, for example, mine is 1:0:0, yours maybe something similar.

---

### Post by cobolt01 on 2007-10-14
It says PCI 1:5:0 or something. But I tried reconfiguring xorg by moving my original xorg.conf and using xorg-reconfigure or something, hoping that it would detect the settings automatically.
But that would maybe make sense, since both the generic drivers and the official drivers make no diffrence to whether or not X starts.

---

### Post by PmDematagoda on 2007-10-16
Change the address to either 2:0:0, 1:0:0 or 1:1:0 using:-

```
sudo dpkg-reconfigure xserver-xorg
```

And see if that solves your problem.

---

