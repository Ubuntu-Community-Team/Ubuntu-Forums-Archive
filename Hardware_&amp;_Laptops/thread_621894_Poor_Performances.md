---
title: "Poor Performances"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by ierpe on 2007-11-24
Hi, I recently switched from a Win2k to a Ubuntu 64bits.

I am playing UrbanTerror and Tremulous, 2 open source game mods from Quake3.
They were working fine on Win2k, but with Ubuntu the performances are really bad. It's not even playable...

Is it because its a 64bits os and the games are made for a 32bits architecture?

I tried to kill gnome and launch them in command, but I have an error saying it cannot load the OpenGL module and the game won't start...

Any Idea/Solution?

My graphic card is a Radeon 9200. I read in the Ubuntu doc that the default radeon driver should work fine. I tried to install the ati drivers anyway and gnome crashes everytime so i'm still using the system default radeon drivers...

Help Plz!!

---

### Post by Aniongap on 2007-11-27
Is your PC 64 bit architecture?

If  it is not, you should install ubuntu for 32 bit architecture. Installing 64 on 32 cause a bottle neck fenomenon in processes, that slows up system.

For better performance you can always try to use

sudo sysctl -a | sort | more
take a look at kernel.threads max.

You can try cut down threads, for smaller but faster peaces of processes.

Try out:

sudo sysctl -w  kernel.threads-max="number"
(for example 13000)

and then try to play. If something fails, when you restart pc, threads return to previous mode.

---

