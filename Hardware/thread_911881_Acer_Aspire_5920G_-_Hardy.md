---
title: "Acer Aspire 5920G - Hardy"
date: 2008-09-06
forum: Hardware
---

### Post by spegru on 2008-09-06
I had this laptop working fine with gutsy but since I upgraded it to Hardy I am stuck with a 640x480 resolution.
It has an Nvidia 8600 graphics card and I have tried a variety of drivers including Envy. But whatever I do I am stuck with the same resolution

By the way the screen is fine if i boot from an Ubuntu hardy or OpenSuse 11 Live DVD - so it is definitely something to do with my setup - but I really dont want to install from scratch.

Please help..

:(

---

### Post by Bucky Ball on 2008-09-06
Try in the terminal:

**sudo nvidia-new-glx**

or in Synaptics you can find it.

You can also download a settings gui. Think that is

**sudo apt-get nvidia-settings**

but probably also in Synaptics.

---

### Post by spegru on 2008-09-06
Thanks. I tried that but it made no difference
Even nvidia settings shows a max resolution of 640/480

sudo nvidia-new-glx is not a known command. I assume you meant sudo apt-get install nvidia-new-glx. I tried that and unfortunately I was left with the ubuntu graphics rescue screen and had to choose another driver - so back to 640/480 again.

help again please...........

---

### Post by Bucky Ball on 2008-09-06
> **spegru said:**
>  I assume you meant sudo apt-get install nvidia-new-glx. I tried that and unfortunately I was left with the ubuntu graphics rescue screen and had to choose another driver - so back to 640/480 again.

help again please...........

Correct. Now did you try the second, correct command I gave to get the setting gui for the nvidia?

---

### Post by spegru on 2008-09-06
Thanks again. In fact I had already tried nvidia-settings but it did not bring up any other resolution options.
(incidentally that command should have been **sudo apt-get install nvidia settings**, to install, and **sudo nvidia-settings** to run it)

However in any case, thinking about it did cause a small brainwave. As I mentioned, the ubuntu live dvd did run the graphics fine. So I ran up the live dvd and extracted the xorg.conf from /etc/X11/ onto a USB memory stick and then booted normally. I then copied the xorg.conf from the stick into /etc/X11/ as root. 

Presto it works!

However there are still some oddities. 

1. In Kubuntu mode (I installed kubuntu-desktop on top of Ubuntu so I have the choice), there is a full list of different resolutions - but in Ubuntu mode there is _only_ 1280/800.
2. The other issue is I cant sucessfully install the nvidia proprietary drivers, so as to get compiz etc. I tried sudo nvidia-xconfig
but it killed the screen down to ubuntu recovery mode again.

So only 90% fixed - although much better than before. :)

I suspect the nvidia driver is incompatible with my kernel. (and there is no sign of the 'install proprietary drivers' icon that you normally get from a fresh install)



*Luckily I now have a known working xorg.conf to revert to if needed. It could be a good tip - using a known working live dvd to extract an xorg.conf file *

---

### Post by Bucky Ball on 2008-09-06
Probably a silly question as you seem probably more on top of it than I, but have you got the ubuntu-restricted-extras installed?

[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%208.04]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%208.04")

Might cause some change of scenery ... :)

---

### Post by 4Bhere on 2008-09-20
Hi
I've got the same equipment and recently did a new install using the Nvidia-new restricted drivers. The old resolution problem you have, has been fixed with the latest revisions.  I am operating compiz (and git-compiz on a separate install) at a resolution  of 1280 x 760 with no need for native drivers.  Maybe a fresh install may solve your problem or follow good advice above.:guitar:

---

### Post by spegru on 2008-09-29
Thanks. I'm not sure how that relates to what I did - which was to boot from a live dvd (which was fine) and copy the xorg.conf file from it. Maybe kind of basic but it works.
Maybe your idea is better but also maybe the system will update itself anyway?

spegru

---

