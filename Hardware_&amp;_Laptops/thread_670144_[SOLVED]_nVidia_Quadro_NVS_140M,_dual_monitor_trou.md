---
title: "[SOLVED] nVidia Quadro NVS 140M, dual monitor trouble"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by vreemde eend on 2008-01-17
Hi,

I've been running Ubuntu Gutsy for a while, without major trouble. But today I tried to attach an external monitor. Which I thought would be an easy thing... but I ran into some issues with the Nvidia driver and the screen resolutions: I'm not able to set the resolution of my laptop monitor correctly (now it's 1600x1200 instead of 1920x1200).

I googled a bit and searched the forums, but no real solution found yet. I tried installing nvidia-settings, but I removed it because it caused troubles). I guess you can hear the laughter of my Windows colleagues :-(. 

My setup:
D830 Intel Core 2 Duo T7300 (2.0GHz/4MB/800MHz) with nVidia Quadro NVS 140M
15.4" WXGA (1920 x 1200) UltraSharp Wide Aspect Ratio TFT display

External monitor:
simple 17 inch Dell TFT, vga connection

Anyone knows a solution?

thanks a lot,

Pieter

(I also noted some changes in the gnome interface, adjusting the volume or changing desktop brings up an ugly gnome-like window, instead of the smooth white transparent windows I had before).

---

### Post by overdrank on 2008-01-17
HI and I do not know much about that graphics but are you using the nv driver or nvidia driver? This could be the issue for the trouble you had with nvidia settings.

---

### Post by vreemde eend on 2008-01-17
Well, I'm not that tech-savvy, in the restricted drivers settings I see the Nvidia driver is activated. Don't know whether thta's an answer to your question?

Thanks,

Pieter

---

### Post by overdrank on 2008-01-17
> **vreemde eend said:**
> Well, I'm not that tech-savvy, in the restricted drivers settings I see the Nvidia driver is activated. Don't know whether thta's an answer to your question?

Thanks,

Pieter

HI and sorry, long day at work. You can verify the driver with this command 
```
cat < /etc/X11/xorg.conf |grep Driver
```
What problems were caused by the nvidia-settings?

---

### Post by vreemde eend on 2008-01-18
```

pieter@fernando:~$ cat < /etc/X11/xorg.conf |grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"
        Driver          "nvidia"

```

When I installed nvidia-settings, it was required to remove nvidia-glx-new. I logged out and got a bunch of errors. Ubuntu changed to low resolution mode (or something like that). My resolution was changed to 800x600 and my mouse pointer became an X. So I removed nvidia-settings en reinstalled nvidia-glx-new.

When booting I get a splash screen of nvidia (which I didn't have before I set up the second screen). I still have the resolution problem on my latop screen (external monitor isn't attached). Preferences -> screenresolution says:
```
The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
```
I got this message ever since I attached the external monitor and I set up a second screen in system > administration > screens and graphics. In the latter preference panel, I can't set my screen to widescreen, even if I choose a 1920x1200 LCD panel.

Thanks for helping,

Pieter

---

### Post by vreemde eend on 2008-01-18
Don't know how I managed it, but I got the resolution of my laptop screen back to work. So I tried again to set up the second screen, but then Ubuntu messed up te resolutions of both screens. I figured out that I can change the resolution on the fly if I only have one screen, when the second screen is enabled, I have to logout to apply any changes. 

So I'm glad I got at least the resolution of my laptop screen right, but I would be nice to be able to attach a second screen... .

thanks,

Pieter

---

### Post by overdrank on 2008-01-18
> **vreemde eend said:**
> Don't know how I managed it, but I got the resolution of my laptop screen back to work. So I tried again to set up the second screen, but then Ubuntu messed up te resolutions of both screens. I figured out that I can change the resolution on the fly if I only have one screen, when the second screen is enabled, I have to logout to apply any changes. 

So I'm glad I got at least the resolution of my laptop screen right, but I would be nice to be able to attach a second screen... .

thanks,

Pieter

HI and If I am not mistaken, I use the nvidia-glx-new and I can use nvidia-settings. So have you tried accessing the nvidia settings? ```
gksudo nvidia-settings
```

---

### Post by vreemde eend on 2008-01-18
Thanks a lot, that worked!!! I was able to correctly set the resoltion of both screens. It's a bit confusing there's a package nvidia-settings listed in synaptic, but isn't needed to run nvidia-settings. 

Again, many thanks,

Pieter

---

