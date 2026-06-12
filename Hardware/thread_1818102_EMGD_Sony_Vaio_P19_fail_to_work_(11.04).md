---
title: "EMGD Sony Vaio P19 fail to work (11.04)"
date: 2011-08-04
forum: Hardware
---

### Post by melaz on 2011-08-04
Hi, All.

I have installed Ubuntu Natty Narwhal on my laptop Vaio P19.
After that I have updated all software - apt-get update, apt-get upgrade. Then using instructions ([link]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Emgd_drivers_.28currently_supported.29")):
> 
sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
reboot for the changes to take effect.

After reboot it fails to work, image on screen flickers (in attach). Console works.
What should I do to FIX this problem? Thanks for help.

---

### Post by SMG510 on 2011-10-10
Hi everyone;

I have the same problem here:

Installed Natty on my VAIO-P.  Performance of the default Poulsbo driver was bad so I searched and according to [this wiki link]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/"), I had two options: 1) Install EMGD drivers;  2) Install PSB drivers (outdated); 

So I chose EMGD and installed using the PPA but after reboot it was a total mess!! :(  Just as the picture melaz has attached in the previous post.

Any help is greatly appreciated.

---

### Post by lucazade on 2011-10-11
Hi guys
check this post for emgd in Oneiric

[http://ubuntuforums.org/showpost.php?p=11311770&postcount=4559](http://ubuntuforums.org/showpost.php?p=11311770&postcount=4559)

let me know if it is enough :)

---

### Post by policarpo on 2011-10-13
Hi!

I have the same laptop with ubuntu 11.04 and emgd drivers.
you can correct the problem by replacing the file /etc/share/X11/xorg.conf/10-emgd.conf with this one: [http://paste.ubuntu.com/707476/](http://paste.ubuntu.com/707476/)

I have it working with dual monitor/extended desktop.
There are some issues with the second screen or unity in case you uncomment : #    Option         "Xinerama" "1"
[FONT=Arial]any hints go make it better are welcome.[/FONT]
best rgds

---

### Post by SMG510 on 2011-10-13
Thanks to both LucaZade and Policarpo;

Actually, now that Oneiric is released I'm going to install it on my machine and replace Natty.

@Luca:  As a professional on Intel GMA500 drivers, which driver do you recommend to install on Ubuntu 11.10 ?!
I guess the options are:  1-The new and developing PSB-GFX (no 3D);  2-EMGD;  3-PSB (outdated);

Looking forward to your advice on this.

---

### Post by lucazade on 2011-10-13
For oneiric you can install only emgd and psb_gfx, psb is discontinued because of it requires too many patches to make it work with latest xorg and kernel updates.
Both emgd and psb_gfx perform well, with pros and cons... emgd, that is full featured, is a bit slow in 2D (where psb_gfx is faster), for the rest (opengl, vaapi) is good but not enough to handle unity3d or gnome-shell (not a great deal for me, i'd say the some limits are also in the chip).

---

