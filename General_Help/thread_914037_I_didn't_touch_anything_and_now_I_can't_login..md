---
title: "I didn't touch anything and now I can't login."
date: 2008-09-08
forum: General Help
---

### Post by chrisloudon on 2008-09-08
Ok guys got a bit of a problem here. I'm a bit a off a newbie so bear with me on this one.

After a few failed attempts and much learning I finally got Ubuntu 8.04 installed with Compiz working pretty much perfectly with my ATI Radeon HD2900 card. That was until yesterday when I booted into Ubuntu for the 1st time in a couple of weeks. I'm not sure what has happened since i've been using Visa for other things but my screen has gone to pot and i can't even login. Failsafe terminal is the only session I can work with.

At login my screen resolution has dropped to big blocky mode. My usual is 1080p and the font size for written text or dialogue boxes is only about 2 pixels high so i can't read any message that pops up during login. Once logged on it then bounces me straight back to the login page.

Everything was working perfectly with the 8.7 Catalyst ATI drivers and now its all gone down the pan. Maybe it just punishing me for using Windows...

I've tried reverting to an older xorg.conf (one that i new worked)

I've tried updating to the Catalyst 8.8 drivers

Anyone got any ideas???

Chris

---

### Post by tuxxy on 2008-09-08
If you can pull up a terminal, you could try reconfigure the xorg and install the drivers again

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by chrisloudon on 2008-09-09
Thanks tuxxy, will try that when i get home from work and let you know how it goes.

I have noticed that during the various driver installations and upgrades over the months my current xorg.conf file has developed new content. I'm sure this is perfectly normal but will reconfiguring the xserver completely scrub my current xorg.conf file and start me back with a basic default one.

Also is it worth me trying to remove any drivers used from ATI or the standard restriced drivers used on 1st install before doing this.

And finally, with compiz-emmerald enabled will it ever let me boot to the desktop if i have a graphics hardware / software problem? Being a desktop manager that uses my graphics hardware / software.

Thanks for the help and sorry for all the questions.

Chris.

---

### Post by Sycron on 2008-09-09
I don't know why ATI & nVidia drivers are closed source. I just can't understand.

---

### Post by tuxxy on 2008-09-09
> **chrisloudon said:**
> Thanks tuxxy, will try that when i get home from work and let you know how it goes.

I have noticed that during the various driver installations and upgrades over the months my current xorg.conf file has developed new content. I'm sure this is perfectly normal but will reconfiguring the xserver completely scrub my current xorg.conf file and start me back with a basic default one.

Also is it worth me trying to remove any drivers used from ATI or the standard restriced drivers used on 1st install before doing this.

And finally, with compiz-emmerald enabled will it ever let me boot to the desktop if i have a graphics hardware / software problem? Being a desktop manager that uses my graphics hardware / software.

Thanks for the help and sorry for all the questions.

Chris.

It should return the xorg to a state where the GUI will boot but you will need to renable the correct drivers, you could also try this command first

```
startx
```

Reconfguring the xorg is great for when you have edited config files, and want your default settings back.

> **Sycron said:**
> I don't know why ATI & nVidia drivers are closed source. I just can't understand.

> NVIDIA supports Linux, as well as the Linux community and has long been praised for the quality of the NVIDIA Linux driver. NVIDIA's fully featured Linux graphics driver is provided as binary-only because it contains intellectual property NVIDIA wishes to protect, both in hardware and in software.

---

### Post by Sycron on 2008-09-09
From now on I won't post messages on these forums. It's my intelectual property, and you are stealling from me. :lolflag:
Just joking.

---

### Post by Zorael on 2008-09-09
> **Sycron said:**
> From now on I won't post messages on these forums. It's my intelectual property, and you are stealling from me. :lolflag:
Just joking.
Neener neener! I'm such a software pirate.

Your point carries truth, though.

---

### Post by Sycron on 2008-09-10
> **Zorael said:**
> Neener neener! I'm such a software pirate.

Your point carries truth, though.

If the drivers are closed source, at least they could do something good, that always works.. not that funky drivers that are intelectual property of nVidia.

Open-source means especially ***share***, which is not always caracterized by third-party tools...

---

