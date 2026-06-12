---
title: "[SOLVED] Nvidia and Hardware Drivers question"
date: 2008-08-08
forum: General Help
---

### Post by huxterby on 2008-08-08
I am a long-time Debian user and always install Nvidia with module-assistant. A bit of a command line fan and not very up to date with all these Guis. The last time I tried a Gui was that Automatix thing in Breezy which seriously messed up the system. Put me off a bit.

I haven't used Ubuntu since Breezy Badger and was given a CD by a friend to play with, I must say I am very impressed with the progress, but had some major issues with the Nvidia driver install.

I first tried with m-a, but kept getting a "Using low graphics mode" error at boot. Next was the Nvidia binary from their site, then on to Envyng which really didn't play well at all. I tried removing xorg.conf (quite common in Lenny nowadays what with recent changes etc).

So, I basically freshly installed Hardy and went to:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

My Nvida card is a Gforce Fx 5200 (old but loyal). The guide tells me I need the nvidia-glx driver:
>  nVidia GeForce FX 5200 Yes Yes Yes 3D requires nvidia-glx, see BinaryDriverHowto. 

I followed the link to the Hardy Heron nvidia-glx guide:
> Ubuntu 8.04 Hardy Heron

Go to System->Administration->Hardware Drivers and check the box to enable the restricted drivers for your nVidia card if the option is provided. 

I did this, and rebooted. There is still a red dot which marks the nvidia driver as "not in use".

Is there something else that was supposed to happen when I checked the nvidia driver box, or maybe something else I am supposed to do?

Any advice would be muchly appreciated. Thanks 

Huxterby

---

### Post by ibuclaw on 2008-08-08
perhaps running
```
sudo nvidia-xconfig
```
in the terminal so nvidia can set itself up to how it "thinks" it should run on xorg.

But before you restart X, post the contents of the changed /etc/X11/xorg.conf file here, just incase you run into deeper problems...

Regards
Iain

---

### Post by huxterby on 2008-08-08
Thanks for the prompt reply Iain.

I just performed a system update/upgrade while I was waiting, and this time when I checked the nvidia driver box a popup window appeared and installed the driver.

I rebooted and everything is working great.

It's a bit of a reverse for me this as I normally help new users to master the command line, and here I am being helped with gui's Lol!

The strange thing is that I noticed the nvidia-glx-new was installed and works perfectly, whereas the Ubuntu guide clearly stated that I needed nvidia-glx for this card. 

Anyway, all fine now, and thanks for the quick response.

Huxterby

---

### Post by ibuclaw on 2008-08-08
Ah, at least all is well :)

Regards
Iain

---

