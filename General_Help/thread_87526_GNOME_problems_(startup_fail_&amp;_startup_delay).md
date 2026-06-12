---
title: "GNOME problems (startup fail &amp; startup delay)"
date: 2005-11-08
forum: General Help
---

### Post by dott.malcom on 2005-11-08
Hi All,
it's a week that i'm trying to solve this problem; i saw a lot of different posts similar to my problem but none of them helped me.

The main problem is the following:
When i turn on my laptop and start ubuntu i get into gdm, if i try to login in a gnome session everithing freeze immediatly (no splash, no sound, no panel).
But if i just run an Xfce session before, and make nautilus run under xfce, then i logoff Xfce and try to enter Gnome-Session then it works.

Secondary problem (probably related):
Some applications in Gnome doesn't start normally, they take long time (1 or 2 minutes) to start; for example the network admin tool or gdm config tool etc...

Tried Solutions:
 - Reinstalling Gnome
 - Reinstalling Xorg
 - dpkg-reconfigure gdm

What should i do then?
tnx in advance

---

### Post by Arktis on 2005-11-08
I probably can't help but I have a few ideas.  Perhaps it is nautilus?  Purge your configuration files for nautilus and/or reinstall it perhaps?  Also, does failsafe gnome work?  What happens when you launch nautilus from failsafe gnome?

**Edit:** perhaps it may also help to post the links to those other topics you have mentioned.

---

### Post by Trab on 2005-11-08
hmmmm ive had a similar problem, to see of its the same, after you login, does it show the brown ubuntu screen?
try waiting about 10 minutes there, and see if gnome starts....
my problem started october 29th, i dunno w/e....

---

### Post by dott.malcom on 2005-11-08
gnome failsafe doesn't work.
I've not yet tried to leave gnome starting for 10 minutes but may be it will be in this way. It freezes on the brown ubuntu screen

---

### Post by dott.malcom on 2005-11-09
I tried and is like we said, if i leave it freeze, it works (login) but after about 10 minutes. So? any answer? any solution?

---

### Post by dott.malcom on 2005-11-10
additional trying:

- delete all gnome conf dirs (.gconf .gnome .gnome2 etc)
- Enter with a new user, whose HOME_DIR was empty and Gnome was never used/configured before

The problem remain. Any help? please is really basic

---

### Post by fishy6969 on 2005-11-10
I had this problem - it came from the ATI drivers and my xorg setup.

What graphics card do you have in your laptop?

---

### Post by dott.malcom on 2005-11-10
Intel P4 with NVIDIA GeForce Go5700
(Hp Pavilion zd7000 laptop series)

---

### Post by dott.malcom on 2005-11-10
lasts:
- tried to compile kernel 
- tried solution 4) in the NOTE SECTION of this thread
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")
> 4) If you have an AGP graphic card and your system freezes but you can still move the mouse pointer you will have to do this:
sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" “Off”

EndSection


This will either disable 3d acceleration or make it slower (sorry but I haven't got an AGP card so I haven't tried them myself)

If this doesn't work for you try asking at this Forum and you might be talking to some of the developers of the NVIDIA drivers (there's a Linux section) (it's very useful)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by rjwood on 2005-11-10
You may want to try to install nvidia-glx 

```
sudo apt-get install nvidia-glx
```

I hope this helps

---

### Post by dott.malcom on 2005-11-10
> You may want to try to install nvidia-glx


Already done, also with older release of drivers

---

### Post by dott.malcom on 2005-11-10
reassuming tried solutions:

 - Reinstalling Gnome
- Reinstalling Xorg
- dpkg-reconfigure gdm
- delete all gnome conf dirs (.gconf .gnome .gnome2 etc)
- Enter with a new user, whose HOME_DIR was empty and Gnome was never used/configured before
- tried to compile kernel
- tried solution 4) in the NOTE SECTION of this thread
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
> 
4) If you have an AGP graphic card and your system freezes but you can still move the mouse pointer you will have to do this:
sudo nano /etc/X11/xorg.conf
Add the lines in red at this section of the file:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "Accel" "Off"
Option "AllowGLXWithComposite" “Off”

EndSection


This will either disable 3d acceleration or make it slower (sorry but I haven't got an AGP card so I haven't tried them myself)

If this doesn't work for you try asking at this Forum and you might be talking to some of the developers of the NVIDIA drivers (there's a Linux section) (it's very useful)
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
- sudo apt-get install nvidia-glx (also older driver version)

On a laptop HP Pavilion zd 7000
Intel P4 512mb RAM
kernel 2.6.12
1500MB swap space

None of this worked!
Help ... :confused:

---

### Post by dott.malcom on 2005-11-10
up

---

### Post by dott.malcom on 2005-11-12
re-up

---

### Post by ssam on 2005-11-15
have you checked the date settings?

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by engla on 2006-02-09
I have one part of your problem, some things take horribly long time to run -- the network settings and gdm settings, exactly!

My system was partly hosed by prelink (my best guess), but I made all binaries on the system work again by reinstalling those that didn't. I also reinstalled every library named libg*, so gnome should be clean.

However, no I'm stuck with the same problem -- some things take awful time to launch. [However, login time is fine]

---

### Post by F Cocquyt on 2006-03-12
Same thing over here. But I managed to start when I remove my PCMCIA network cards. (1 ethernet and 1 wlan card). searched the net for a solution but haven't found one yet. :confused:

---

