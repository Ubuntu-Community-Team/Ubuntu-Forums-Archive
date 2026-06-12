---
title: "IBM ThinkPad T21 Cannot autologin, seems that display crashes"
date: 2010-01-09
forum: Hardware
---

### Post by scytherswings on 2010-01-09
My computer is set to auto-login, however during the boot sequence the laptop will freeze and the "bootup image" will become very distorted, the laptop fails to reach the desktop and thus plops me to a login screen (which isn't supposed to happen).
If I try and log in, the laptop will almost get to the desktop like before, but then crash or something and bring me right back to the login screen.

What I know:

Ubuntu 9.10 fully updated.
The laptop has some sort of S3 graphics (cant figure out which) but it is from 2001 or 2002.

What I have found out:
If I use the command "startx" after entering "recovery mode" during the grub boot stage, everything seems to work fine and I can use 1280*1024 resolution. But the problem is, I have to hold down shift and login manually before I can do all of this. And the laptop is using a "software rasterizer" instead of the S3 videocard doing the work. This is a problem because the laptop has only a PIII processor at 1.1 Ghz and any extra load makes flash videos jerky and difficult to watch.

Btw this is only a problem when I dock the laptop, otherwise it usually works fine and uses the "S3 Savage" driver which is built into Ubuntu. Any help is greatly appreciated! Thanks!

ps: when I navigate to /etc/X11 there is no xorg.conf file to be found...

---

### Post by scytherswings on 2010-01-09
Anyone know if logs/which logs would be helpful? This is a major inconvenience to me and I would really like to get it fixed. Thanks

---

### Post by sanderd17 on 2010-01-09
Does this happen with the live cd too?
Dit this alway happen? Or did it just recently begun to do this?

---

### Post by kyuubi777 on 2010-01-09
one of the operating systems on my laptop (rose linux 2009) will only boot into a shell cmd line prompt... i can use the startx command to get a gui, but to boot into gnome, weirdly i have to use the   ~shutdown 0    command
after that i get full gnome DE.

---

### Post by scytherswings on 2010-01-09
This issue just started today, but it only happens when I "dock" my laptop and use the CRT monitor. The laptop's normal screen resolution is 1024*768 and the monitor I'm using is a 15" IBM P76 if that helps. It works best with a resolution of 1280*1024. I'm wondering if the lack of a xorg.conf file is causing this, but I don't know how to fix that...

---

### Post by sanderd17 on 2010-01-09
I've heard from one with a lot more beans than I have that a lot of computers don't need a xorg.conf file anymore. So I don't think this would be the problem and it's quite impossible this would just happen to disapear if you do needed it.

Does that dock also has a power plug? It's cause I'm thinking of an acpi issue. Does it change if you try booting with acpi=off? 

in grub: press 'e' to edit the line and change "quiet splash" to "acip=off". If this works you can update the grub.

---

### Post by scytherswings on 2010-01-09
Yes, the dock does charge the laptop, but how does the power change how the display server acts? It still shows an image on bootup, I get get POST and everything, it just fails right before it gets to the desktop for some reason.

---

### Post by scytherswings on 2010-01-10
So is this possible that its a power issue?

---

### Post by sanderd17 on 2010-01-10
If acpi=off doesn't work it won't be a power issue.
I really don't know what it is, sorry.

---

### Post by scytherswings on 2010-01-11
Alright, well I will work on trying that... It seems that when I start it through the "recovery mode" and then startx myself it works fine. I checked a hardinfo and it said that my system was using a "software rasterizer" whereas when the laptop was having trouble before, it was using the "S3 Savage etc.." driver/rasterizer that was built in to Ubuntu. Does anyone know how to possibly upgrade my driver or change the settings? I think the driver doesn't support resolutions greater than 1024*768, but that's just a hunch.

---

### Post by scytherswings on 2010-01-11
Nope the "acip=off" doesn't change anything at all, but I also observed the monitor switching on and off repeatedly during bootup, which leads me to think that the laptop is trying to output different resolutions or something during bootup... This is a pretty flexible monitor, and can display 1600*1200 if you've got a magnifying glass ready... So I'm pretty certain it's not the monitor...

---

### Post by scytherswings on 2010-01-12
C'mon people! I know you're smart! Isn't there anyone willing to tackle this problem? I can provide as much information as you need. Thanks

---

