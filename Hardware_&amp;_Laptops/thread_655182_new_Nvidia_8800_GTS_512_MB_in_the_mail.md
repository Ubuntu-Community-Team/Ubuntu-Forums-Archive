---
title: "new Nvidia 8800 GTS 512 MB in the mail"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by pondochris on 2008-01-01
I ordered my new video card and it will be here in a couple days.\\:D/  I'm sooooooo excited to be able to play the latest games with decent video I can't even begin to describe.  However...is there anything I can do before I get it (install latest drivers/modules) or should I wait until I plug it in and see what happens.  Anyone else have this card?  Did you have problems with the drivers or did it just work?  

Any insight or helpful links are appreciated.

Thanks in advance.:)):P

---

### Post by Daelyn on 2008-01-01
I have not heard about any issues with the nVidia cards at all, to be honest. Drivers usually work explendid once installed.

> FIrst of all. What graphics card do you have in your computer right now? Is it a nvidia card?  are you running the "nvidia-glx-new" package in that case? If so, shut down, plug in, and start up again. The driver should see the difference and make use of it.

> If you have another graphics card wich uses in the box drivers, just download the "nvidia-glx-new" package and before shutting down the last time before GFX change, write "sudo nvidia-glx-config enable" in terminal to activate use of nvidia driver in xorg.conf.

> In case you use a non-nvidia GFX card that uses restricted drivers, or from somewhere else, uninstall them before you install the nvidia driver. They are linking themselves to different OpenGL libraries and it might mess up your graphics capabilities if you don't (libraries point to the wrong drivers once you've changed GFX card).

IMPORTANT: To do the "sudo nvidia-glx-config enable" live with a different GFX card will only work if you plug in the nvidia card to the same slot as your current GFX card. If your card uses a different port type or is integrated, this will not work.


On the other hand, usually X will complain about wrong graphics card and stuff, and you can still get in to a failsafe gnome. Once there you should able to install the nvidia glx driver and it will detect the new settings and the port for you.

---

### Post by pondochris on 2008-01-01
Thanks for the info! My current gfx is an integrated nvidia 6100.  Are there any tricks I should be aware of when switching from onboard to pci express?  Will I have to disable the OB chip or anything?

---

### Post by tgalati4 on 2008-01-01
The 8800 uses a lot of power.  You should be able to turn off the on-board chip in the BIOS.  Your power supply may complain if it is not up to snuff and that will cause all sorts of weirdness.  You probably need a 350-watt minimum and 500-watt (desirable).

---

