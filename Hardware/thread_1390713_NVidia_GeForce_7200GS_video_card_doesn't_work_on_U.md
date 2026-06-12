---
title: "NVidia GeForce 7200GS video card doesn't work on Ubuntu 9.10 Karmic Koala"
date: 2010-01-25
forum: Hardware
---

### Post by Fiable.biz on 2010-01-25
Hello.

I'm new to Ubuntu, coming from Mandriva Linux.
I have Ubuntu 9.10 Karmic Koala 64 bits installed (default installation). My screen is a Philips 201B4, 21" (20 VIS) VGA, supporting 1 920 × 1 440 but set to 1 600 × 1 200 on Ubuntu's "display". It works with not video card.
I plugged the NVidia GeForce 7200GS video card, and plugged the screen wire on the VGA output of the card, got Ubuntu's logo, then the login page was not displayed properly: there was only the arrow on a striped fuzzy grey background. The arrow could move following the mouse. If I pressed "Enter" 3 times, the arrow became the round waiting symbol. I tried again and got the same symptoms except that the background was multicolour, divided in striped squares. A third try gave me the first time result.
Then I unplugged the card and, through Ubuntu software centre, I installed NVidia driver for X.Org, last version (185), after checking that GeForce 7200GS was in the messy list of compatible video cards. I noticed that, on NVidia web site, the last version is not 185 but 190.
I plugged the card again, but the result was exactly the same: no proper login page.

Any advice will be welcome.

---

### Post by cascade9 on 2010-01-26
I assume that it worked under Mandriva?

---

### Post by Fiable.biz on 2010-01-27
Thank you very much for coming here. I don't remember the problem I had a few months ago with Mandriva but I guess I couldn't make it work either.

---

### Post by jocko on 2010-01-27
Just installing through software center is not enough, you need to make an x configuration file (/etc/X11/xorg.conf) that tells xorg to use the driver. By using the hardware driver manager (System-->Administration-->Hardware drivers) this is done automatically, but with any other method you'll have to do it manually.

Can you get to a virtual terminal (press Ctrl+Alt+F1)?
In that case, log in and stop gdm:
```
sudo service gdm stop
```
Then generate a x configuration with:
```
sudo nvidia-xconfig
```
And start gdm again:
```
sudo service gdm start
```

---

### Post by wandalalakers on 2010-01-27
nm

---

### Post by Fiable.biz on 2010-01-28
Thank you very much Jocko. What I forgot to do is to save xorg.conf ! So now I have problems with and without the video card! nvidia-xconfig doesn't backup xorg.conf.
When launching nvidia-xconfig I had got the message "Warning: Unable to locate/open X configuration".

With the card, I can now log in, but the screen is duplicated: in the middle, the things of the left appear again, unstably. Some stuff of the right, specially the "display" icon of the upper bar, don't appeear. If I open a window, it's also duplicated. On the bottom, the bar and, if present, the mouse, are in many copies. It seems that the size of the screen is not understood.

Without the card, the bottom was also in multiple copies. The only way I got read of that is by deleting by hand the "Device0" (NVidia card) section of  xorg.conf and its reference in the "screen" section. So now it works with no card, but only as 640 x 480 pixels, and the "display" tool of Ubuntu doesn't propose a better definition.

---

