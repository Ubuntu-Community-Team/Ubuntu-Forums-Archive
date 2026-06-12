---
title: "[SOLVED] NVidia 9600gt proprietary drivers not loading"
date: 2008-06-22
forum: Hardware
---

### Post by revpfil on 2008-06-22
Hi, after installing the drivers from nvidia.com, they are not loading for some reason, and restarting X brings up the failsafe dialog. Any suggestion what to do?

---

### Post by hal10000 on 2008-06-22
Maybe you have forgotten to purge the nvidia-glx driver packages from your system.
You can open synaptic and search for "nvidia-glx" (without quotes) and purge (not only remove) all packages that start with [COLOR="Red"]nvidia-glx ...[/COLOR]
There are other requirements which you may see from here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490").

In the upper link, scroll to the Debian/[K]Ubuntu section and follow the instructions, then you might get it work.
The most important point is to purge the nvidia-glx packages.

---

### Post by sdennie on 2008-06-22
If you are using the downloaded drivers, you will also have a problem that, every time a major kernel update comes out, the drivers will stop working.  To prevent that from happening, try this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Edit:
Of course, you will want to make sure the drivers are working perfectly before using that guide.

---

### Post by OddishLump on 2008-06-22
revpfil was actually asking this for me.  We spent several hours last night going over different methods of trying to get these drivers to work properly.

The card is an EVGA NVidia 9600GT 1GB.  I made a fresh install of Ubuntu and removed nvidia-glx, then downloaded the 177.13 drivers.  I stopped X and I installed the drivers and then I started X.  [This](http://i28.tinypic.com/213pvo0.jpg) is what comes up when I start X.  That box at the bottom is the notice that X can't detect my driver/monitor so it's loading in low-graphics mode.  lsmod DOES show the module is loaded.

Hal10000: I have met those requirements.  Unfortunately, it still refuses to work.

---

### Post by hotweiss on 2008-06-22
You are in luck, Envy has the new Nvidia drivers as of June 11th.

1. sudo apt-get remove nvidia*
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by OddishLump on 2008-06-22
hotweiss: I tried your method and am still getting the same problem.  :(

I expected some problems with the 9600 when I bought it, but if I had any idea that this would happen I never would have.  :/

---

### Post by Neo0351 on 2008-06-28
here's how i got mine working
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by revpfil on 2008-06-28
It turns out it was a hardware problem with the card itself. It has been replaced and is working fine now.

---

