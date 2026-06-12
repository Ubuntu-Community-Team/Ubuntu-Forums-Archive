---
title: "NVIDIA Optimus doubt"
date: 2015-03-16
forum: Hardware
---

### Post by kosak2 on 2015-03-16
I need to know something guys. Wanting to ditch Windows and converting to Linux i'm at one step of creating the bootable media.I just wanna know if with the newest driver of NVIDIA Geforce 820 m (ver 446 i think) Linux will be able to recognize when to use Nvidia card and when tou use the intel, weaker one. It's a normal Optimus laptop, Asus X550LDV, i7 2.00GHZ, Intel Graphics HD and Nvidia Geforce 820m.
All help and knowledge would be appreciated, as I really dont like the idea of using Bumblebee or prime, I would like to install drivers and get it going. 

Thanks in advance

---

### Post by kosak2 on 2015-03-16
Confusion... i want to use prime not bumblebee, just auto switching is it possible?? and i can turn off the intel weaker card, so its mux system and nvidia is 346 driver version

---

### Post by Yellow Pasque on 2015-03-16
> I just wanna know if with the newest driver of NVIDIA Geforce 820 m (ver 346 i think) Linux will be able to recognize when to use Nvidia card and when tou use the intel, weaker one. 
No. You can't just install the Nvidia driver and have it automatically/seamlessly switch back and forth based on load (like you can on Windows).
The proprietary driver may allow you to use Bumblebee to manually run demanding programs on the nvidia card.

As for prime, it should allow the same thing as Bumblebee (manually switching) using the open-source nouveau driver. I don't know where the nouveau driver is at in terms of being able to run newer cards (Fermi/Kepler/Maxwell) at full clock speeds. I think it's still experimental at best: [http://www.phoronix.com/scan.php?page=news_item&px=MTc3NDU](http://www.phoronix.com/scan.php?page=news_item&px=MTc3NDU)
[http://nouveau.freedesktop.org/wiki/Optimus/](http://nouveau.freedesktop.org/wiki/Optimus/)

---

### Post by kosak2 on 2015-03-17
So, no Linux for me now... Too bad man

---

### Post by Keith_Helms on 2015-03-20
My laptop has the Geforce 860m in it, which I assume is newer than the 820m.  I'm running Xubuntu 14.04 and have the nvidia-prime and nvidia-331 drivers from the repository installed.   I'm able to use the Nvidia X Server Settings application to switch back and forth between using the Intel graphics card and the Nvidia 860m.  I can only use one at a time.  There is no automatic switching back and forth between them.

---

