---
title: "Freezing and Crashing 9.10 Karmic, ATI X1400"
date: 2009-11-02
forum: Hardware
---

### Post by JHumphrey on 2009-11-02
I installed 9.10 today, and about every 1-45 minutes everything will freeze. I get two types of freezing, I either get a window's freeze, where all that is responsive is the mouse cursor that slows down and it's position is updated infrequently, or I get the freeze where everything freezes including the mouse.

I suspect it has to do with my ATI x1400 graphics card in my laptop. I have enabled ctrl-alt-backspace but that doesn't do anything, so I am forced to do a hard shutdown.

I also did the system testing thing, and it seemed like everything worked.
So, how can I fix this?

Gateway laptop, ati x1400 gfx card, vanilla install of 9.10 karmic koala

edit: as a result of all this hard shutting down, audio has broken, and some dependencies have also broken for something I was trying to install

---

### Post by Deepstair on 2009-12-13
I am having the same problem. Does anyone know how to solve this? It's getting worse even to come a far to get to the forums is tough. Having this since yesterday and been with ubuntu for a month and a half. Please help!
Sorry for bad english.

Have :
Intel Pentium IV 2.8GHZ
Ati Redeon 9600 128 mb
1gb ram

---

### Post by drewster1829 on 2009-12-19
I've been having a similar problem, but I just have Intel's integrated graphics on an old Toshiba laptop with a Pentium M (I think it's the Intel 915 Express Graphics Controller), and I've been having the problem since 9.04 or 8.10.  I'm running a custom install (openbox, pcmanfm, wicd, fbpanel, leafpad, abiword, mplayer, no GNOME, no metacity, no network manager, etc...), but I don't think this is the problem.

Almost always, the entire GUI will freeze except for the mouse pointer (which I can move around, but clicking does nothing), and it quits accepting any keyboard input (I can't even turn the Caps Lock LED on by pressing it).

Sometimes when I press the power button, it'll do a clean shutdown, othertimes I have to hold it to do a hard power-down.

I'm thinking it has something to do with firefox because it seems to have started when I started using firefox 3.6 alpha 2 (now I'm upt to 3.6 beta 5, but I'm having the same problems).  Maybe it's an add-on?  

Anyway, I've never had the freeze if firefox isn't running (but firefox is almost always running, so that doesn't really help much).

---

### Post by crazysubguy on 2009-12-28
I'm having the exact same problems.  My hardware is a Gateway CX210x with x1400 mobility ATI graphics.  I can boot into Karmic most of the time and it freezes with the above symptoms fairly rapidly.  However, I still have the original Windows XP loaded and I can boot into that and have no problems whatsover.  It's been almost two years since I've used XP but it's the only way I can use the laptop right now.

---

### Post by Pithikos on 2010-02-10
Same problem though I have ATI Radeon 9600. Mouse can move around but anything else is just frozen.

Just found out that one way to make the freeze occur is to try resize the window of VLC while a video clip is playing.

---

### Post by brawd on 2010-02-11
Me to I'm sorry to say.

Gstreamer gone missing.
Mplayer is just a couple of bits of clipart on the desktop.
Everything was fine with Ubuntu 8.04. Problems started with new install of 9.10

Graphics are Nvidia.
Asrock AliveNF6P MoBo
Ubuntu 9.10 64bit.

brawd

---

### Post by itchaka on 2010-02-16
I also have x1400 mobility in my laptop with karmic 9.10 and the radeonHD drivers work well for me, had to edit the xorg.conf file after installing driver to manually set it to readeonhd.

My laptop was doing the exact same thing, shutting down after 1 to 45 minutes, so i opened it and the gpu fan was almost not turning, so swapped it for an old p3 cpu fan it now its very stable, maybe you have same problem. Does the image start to get messy before it freezes ?

---

### Post by bambanx on 2010-03-25
please put the link tutorial for install the driver for the ati x1400 on ubuntu 9.10 64bits .
thanks.

---

