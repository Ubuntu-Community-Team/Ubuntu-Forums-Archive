---
title: "Can't set 1080p"
date: 2011-04-21
forum: Hardware
---

### Post by cogadh on 2011-04-21
I'm trying out Xubuntu as a lightweight HTPC for my new HDTV and I'm running into a "showstopper" problem. After installing the Nvidia drivers, my resolution was automatically set to 1920X1080 interlaced, which causes issues for the TV since it is expecting 1080p (everything has a kind of "quivering" effect on it). I can't find any way to change it from interlaced to progressive, either through the GUI (including the nvidia-settings app) or through manually editing my conf files. I'm probably just missing something blatantly obvious, but if anyone has any suggestions on how to fix this, it would be greatly appreciated.

System specs (yes, I know its a piece of junk):
P4 2.0GHz
Nvidia FX5200 256MB (173 drivers)
512MB RAM
120GB IDE drive
Vizio E371VA HDTV

EDIT - Almost forgot, switching to the older driver package also did not work as it prevented me from setting a resolution higher than 720P, which my TV does not support.

---

### Post by LinXNut on 2011-04-21
I am not sure if this helps....I have a pretty crappy laptop, so I know nothing about HD and progressive. :P

[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

Good Luck! :P

---

### Post by cogadh on 2011-04-21
Thanks, but I'm not actually using TV out. Since this is a LCD HDTV connected via DVI->HDMI, the system simply identifies it as a really large monitor and doesn't even use any of the tv out functions, nor should it need to.

---

### Post by SeijiSensei on 2011-04-21
Use the NVIDIA X Server Settings application and check that you're using a 60 Hz refresh rate.  Also check the TV and see if you can force it to use 1080p.  Does it have any special modes for computer connections?  I think it's more likely the problem is with the TV rather than the video card or driver.

---

### Post by cogadh on 2011-04-22
Definitely not the TV, it worked fine while connected to the same machine running Windows, so I'm certain that the hardware (including the video card) is capable and already connected correctly. It is already doing 60Hz refresh rate, but the problem is not forcing the TV to do 1080p (it doesn't need to be forced, it wants to be doing 1080p), the problem is the video card driver or X (not sure which is really at fault) will only do 1080i and won't let me change it to 1080p via any means I have tried, including the nvidia-settings application.

---

### Post by K_45 on 2011-04-22
This is because your card doesn't support 1080p - look at the product info guide on nvidia's site. That GPU is HDTV ready, but that is it.

---

### Post by cogadh on 2011-04-22
Yes it does support 1080p (that's what "HDTV ready" means). As I already stated above, I had the TV connected to the same machine running Windows and the card had no problems with 1080p at all. In fact, it automatically set that as the resolution immediately upon boot. Unfortunately, the machine was too slow with Windows and all its crapware running on it, so I'd like to try it with Linux to see if it is any better. So far it isn't.

---

### Post by K_45 on 2011-04-22
Check the product overview on the left:  [http://www.nvidia.com/page/fx_5200.html](http://www.nvidia.com/page/fx_5200.html)  support for 1080i - which is HDTV "ready" but it doesn't fully support 1080p.

---

### Post by cogadh on 2011-04-22
Again, it doesn't matter what that says, it's wrong. I think you're reading/interpreting it wrong anyway, that 1080i reference has nothing to do setting the screen resolution, that has to do with Mpeg-2 decoding only. As I have already explained twice now, I already had this machine with this video card running at 1080p in Windows with no problems, so I know with absolute certainty that it can and will do it, it just seems to have an issue doing it in Linux and I'd like to figure out why.

---

### Post by K_45 on 2011-04-22
Well the Xorg log should have more information on the modelines your card supports, which you should also be able to force.

---

### Post by cogadh on 2011-04-22
Xorg only has in it what was automatically put there during the installation of Ubuntu, nothing more. I have already tried "forcing" it to do this, the problem is, for some reason, either the driver or X refuses to do anything other than 1080i. I can't even set the lower standard resolutions that my TV supports, like 1024x768.

---

