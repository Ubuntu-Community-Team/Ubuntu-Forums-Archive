---
title: "screen resolution problem - 800x600 max on laptop"
date: 2008-08-17
forum: Hardware
---

### Post by dgapitts on 2008-08-17
Hi there,

I am running Ubuntu 8.0.4 (desktop edition) on my laptop (intel 386, 1GB ram with onboard graphic card) but can not get the screen resolution above 800x600 - not very practical.

The laptop graphics card is "SiS MIRAGE3".

Currently Ubuntu has selected a "vesa graphic driver" and "generic pnp monitor" for my (novatech) laptop.

Can anyone suggest how I can increase the screen resolution?

Thanks

Dave

---

### Post by spacedoggy on 2008-08-18
is it like this since install or after you changed graphics settings?

I have an ATI chipset but this happened to me when i was messing with video settings, it got stuck on low res.

I made a backup copy of the file /etc/X11/xorg.conf and then deleted it, after a reboot, X had rebuilt the file and restored my available resolutions

if it's like this from you first install ubuntu, try editing /etc/X11/xorg.conf changing the driver to vesa and adding desired resolutions. again be sure to keep a backup version of the file.

SD.

---

### Post by cdtech on 2008-08-18
Do you have your "proprietary drivers" and "Software restricted by" selected within the "System > Administrator > Software sources". Then select the Hardware driver within the "System > Administrator > Hardware drivers" section.

Hope this helps.......

---

### Post by dgapitts on 2008-08-18
I did try rebuilding the /etc/X11/xorg.conf file (following instructions I found in the ubuntu help wiki and this forum) however it always seems to come back to the vesa graphic driver?

I also tried manually adding a higher resolution in the x11.conf file again following online instructions but this didn't work for me :(

Thanks for the suggestions, I may try manually adding a higher resolution again.

---

### Post by dgapitts on 2008-08-18
Unfortunately I'm not sure there is a linux/ubuntu driver for the "SiS Mirage 3" graphics card? I found another old post where someone with another novaech laptop see to be struggling with a driver?  Although I think they had higher resolution (1080x800?). 


[Could my laptop screen be a factor too?]

---

### Post by dgapitts on 2008-08-18
I have just checked my laptop again, as per cdtech's instructions:

1) "proprietary drivers" and "Software restricted by" ARE selected within the "System > Administrator > Software sources"

2) Within "System > Administrator > Hardware drivers" it says "no proprietary drivers are in use ..."

Any ideas ???

---

### Post by rhapsodyinblue on 2008-10-07
I can confirm I'm having the same problems with the Sis Mirage 3. I've been scouring the net over this one but I haven't solved it yet.

---

