---
title: "Graphics card on Acer Aspire 3000"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by fenno182 on 2007-05-03
Hi i am new to ubuntu and i am so far impressed. The only problem i have now is the graphics card. The wifi did not work but scanning these forums i managed to find a fix.

I have an Acer Asire 3000 laptop. the graphics card is a SIS M760GX 

I wondered if someone could talk me through installing the drivers for this card so i can have a resolution greater than 1024x768 and also enable desktop effects and play games.

hope someone has the same laptop and working graphics.

thanks

This is now sorted! i ran the /etc/X11/xorg.conf and selected SIS then accepted all defaults and added the resolutions i wanted. for some reason this didn't work earlier tried it now restarted and all fine.

---

### Post by bakermiller on 2007-05-31
...but i'm sure you don't have 3d acceleration....do you ? i don't :(

SiS won't release their drivers as open source. acceleration worked under windows, but just crashes my computer when i try something somewhat 3D intensive under feisty... i've been fighting with this for over one month now... i gave it up. 

A super-linux-user-friend says he will fix my kernel and make it work some day. i can't wait. for now i can't run google earth or any 3D screensaver or enven | grep glx info, it just kills my computer :P

i can't wait for SiS to release their drives. I may have to complain to them that the hardware i bought from them is not compatible with the OS i CHOOSE to install.

i tried this guys SiS stuff, but it still does'nt work...

[http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml)

---

### Post by carlossl on 2007-06-24
I have an Acer Aspire 5000, and this is what worked for me (I think the aspire 3000 and the 5000 are almost the same):

```

 sudo dpkg-reconfigure xserver-xorg

```

Follow the instructions carefully, if you're not sure about something, leave it blank or with the default answer. Be careful when you get to the part where you select your resolution, you should know previously which one you have to use. And by the way, your color depth is 24 bits (what in windows we know as 32 bits).

---

### Post by whorobj on 2007-07-01
thanks

---

### Post by Grindlay on 2007-08-18
Yep, worked for me too on my Aspire 3004WLMi AMD64 Sempron
Not 100% sure what the native res of the widescreen is, but 1280x800 looks OK.
*-display
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I used:
sudo dpkg-reconfigure -phigh xserver-xorg
Didn't need to change my sis_drv.so, in fact when I did, GDM wouldn't start.
X Window System Version 7.2.0

G.

---

### Post by elvi87 on 2008-05-29
I have tryed:

sudo dpkg-reconfigure xserver-xorg

but i get:

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process

what to do ?

---

