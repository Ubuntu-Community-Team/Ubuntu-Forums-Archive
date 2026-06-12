---
title: "I need video cards recomandations"
date: 2009-03-13
forum: Hardware
---

### Post by cgfc on 2009-03-13
hello ubuntu friends. I'm very new with linux (i'm an ex-windows user) and I'm having troubles with my video card configuration.

I have a Nvidia 5700, and Ubuntu detects it well, but I cannot make the dual view work.

I've been reading a lot of manuals from Nvidia and Ubuntu and I've changed the xorg.conf hundreds of times, but I have allways the same result (when I open the X Server, the TV monitor is disabled), so I think that maybe the best option is change the video card. So my big cuestion is: Can you recommend me a video card with TV OUT that works excellent with Ubuntu, and haven't troubles with configuration?

Thanks!!!

---

### Post by Naiki Makuri on 2009-03-13
.

---

### Post by lesemi on 2009-03-13
hi

- which version of ubuntu have you installed.
- i don't recommend investing in new hardware if the hardware worked previously in windows.
- in intrepid - configuring xorg.conf can be difficult from my experience - i work with dual monitors from my laptop at work and once in a while at home.

one solution you may want to try is to install the nvidia driver using envyng. (in the repos under hardy and intrepid)

your crt monitor will be off when you boot - you need to go through the nvidia-settings to activate dual monitors when you need it.

---

### Post by cgfc on 2009-03-13
> **lesemi said:**
> 
- which version of ubuntu have you installed.
- i don't recommend investing in new hardware if the hardware worked previously in windows.
- in intrepid - configuring xorg.conf can be difficult from my experience - i work with dual monitors from my laptop at work and once in a while at home.


-i have ubuntu 8.10 :KS
-yes, the card works perfect in windows :o
-modify the xorg.conf it's a nightmare :(

another tip, is that I have try with all the dirvers that ubuntu offers, and also I installed the one that is in the Nvidia page, but no results, i just get TV monitor is disabled.
I really don't want to come back to windows, so I think that maybe, if I change the hardware is a good option, but if anybody could guide me I would be great! :D

thanks to all for the quick reply!!

---

### Post by lesemi on 2009-03-20
Hi cgfc

Have you tried the script envyng?
i find it's a very effective way to install the driver properly.

first copy your xorg.conf in case something gets muffed up.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

sudo apt-get install envyng-core envyng-qt

then do crtl + F1 to get out of x

sudo /etc/init.d/kdm or gdm stop

sudo envyng -t

install the recommended driver

reboot

once you are back in your session - the driver should be installed and functionning properly

sudo nvidia-settings
and find your crt monitor - you can then activate it.

Sorry for the late reply - i haven't checked the forum a bit.

---

