---
title: "nVIDIA Problems, resolution, visual effects, etc..."
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by doublen675 on 2009-11-02
Ok, I installed Ubuntu 9.10 as a dual boot setup alongside Windows XP.  My pc isn't too old, here are the specs:

AMD Athalon X2 Dual-core processor 3800x (2GHz)
3 GB of RAM
320 GB HD
nVidia GeForce 6100 Graphics card (Possibly the Problem)

My resolution will not go beyond 800x600, I have tried the terminal commands like:
xrandr -q
and
xrandr -s 1280x1024

No joy.  So, is my graphics card too out of date to get a proper driver for?  I can live without the visual effects, but I would like the resolution higher.
When I go to: system/administration/hardware drivers I get absolutely nothing, meaning there are no proprietary drivers listed.  When I booted from the CD it found 3 different drivers I could install, but now nothing.

Any suggestions?

Thanks in advance.

---

### Post by Kareeser on 2009-11-02
Give this a try:

```
sudo apt-get install xserver-xorg-video-nouveau
sudo shutdown -r now
```

---

### Post by doublen675 on 2009-11-03
tried that now, no luck.  I downloaded the driver from the Nvidia website and when I try to install it says something about a "Root" ????  I am not computer dumb, but this is my first experience with a Linux based os.

---

### Post by presence1960 on 2009-11-03
Try using Envyng to get your Nvidia driver. You can install envyng-core and envyng-qt from Synaptic Package Manager or through terminal:

```
sudo apt-get install envyng-core
```
&
```
sudo apt-get install envyng-qt
```

You can then access Envyng through Applications > System Tools > EnvyNG

or through terminal ```
sudo envyng -t
```

---

### Post by doublen675 on 2009-11-03
I will try it....Standby

*edit*

Tried it and here's what I got...

---

### Post by presence1960 on 2009-11-03
I am not sure under which repository Envy is, but I would make sure Medibuntu is enabled.

---

### Post by doublen675 on 2009-11-03
Tried to download envyng-core from softpedia.com and here's what I get... Second image is when I try to do it through the software center by copying the link and pasting it in  firefox.

---

### Post by doublen675 on 2009-11-03
> **presence1960 said:**
> I am not sure under which repository Envy is, but I would make sure Medibuntu is enabled.

You are the man!  That may have fixed it.  I downloaded and installed Medibuntu and when I checked to see if any drivers were listed it showed me the ones needed for my Nvidia Graphics card.  Downloading now....Slow internet...I will update this thread asap.

THANKS!

---

### Post by doublen675 on 2009-11-03
OK, so I downloaded and installed the Recommended driver.  Restarted Ubuntu and when I got to the login screen, the resolution now looks spot on.  However, when I log in, my screen goes black and I get the "Out of Range" error you usually get when you use the wrong resolution.  Only problem is it will not revert to a working resolution and I have no idea how to fix it.

---

### Post by doublen675 on 2009-11-03
Bump):P

---

### Post by doublen675 on 2009-11-04
So...Anybody?

---

### Post by presence1960 on 2009-11-04
Sorry that I am out of ideas. I had one but it won't work in 9.10. I booted into recovery mode but xfix is no longer an option in 9.10 recovery mode. Someone will come along who is more knowledgeable in the graphic area then I am.

But using 9.10 your python should be 2.6.4- see my screenshot. That is what one of your screenshots are complaining about. Have you updated your system from System > Administration > Update Manager?

---

### Post by doublen675 on 2009-11-04
That was the next thing on my list.  While I was updating my Nvidia driver, my update manager popped up and had a huge list of updates that I needed to download.  I figured I would do the driver install, restart and then get on with the updates while I was playing around with the graphics.  So it is probably missing a bunch of updates which may be causing the issue.  I am wondering if there is a way to revert the system back to before the driver install, kind of like how you can system restore windows.  ?????  Hmm...

---

### Post by Yamakasi on 2009-11-05
this is my first contact whit ubuntu(linux) so im new here and dont know a lot about it.few days ago installed 9.10.I use Nvidia geforce4 420GO and decide to instal nvidia-glx-96, after reboot got black screen so i reinstall 9.10 from cd.Now im look for way to  backup system  before install graphic card.
I found program called simple backup config/restore in Ubuntu Software Center but cant install them, and other one called partimage in Synaptic Package.I have tried partimage but get error when  tried to unmount partition.
"umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof( 8 ) or fuser(1))"
Anyone know how to fix it?
p.s sorry for my bad english but i never lern this language before

---

