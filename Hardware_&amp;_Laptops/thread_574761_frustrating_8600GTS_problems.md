---
title: "frustrating 8600GTS problems"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by MasamuneX on 2007-10-13
So here's the story guys,
I recently came into some money through work and such.  I took some of this money and invested it into my computer.  So now I'm sitting atop a shiny new nVidia 8600GTS and 3GB of RAM.  And all was well in the world...

...Until my HD toasted itself.  So I order me up a shiny new Maxtor 250GB HD, Partition it for dual boot (XP and Ubuntu) and started setting things up.  For the first portion I couldn't even get Ubuntu to recognize the card.  I turned off the comp., pushed down on the video card a little more to ensure proper seating and restart.  Now Ubuntu sees the card.  But here's my problem and I was having this before the HD crash.  I can't get the drivers to stay installed.  I'm somewhat new to Ubuntu, but I was able to install the drivers from nVidia's website (even logged in as root and shutdown GDM to install this bad boy).  I previously tried using Envy but when I start up after using that I get a text dump about Xserver or something not being able to start.  I use the other Ubuntu choice (ends with 15 instead of 16; what's that about :confused: ) and I can get it to start up GDM fine and everything else, but my only resolution choice is 640x480.  Frustrating to say the least.  Anyone have a solution?

Cliff notes:
-New 8600 GTS card doesn't run correctly
-Problem is driver related
-Drivers won't stay installed
-Why are there two choices for Ubuntu at GRUB?
-Envy didn't work and neither does the official drivers.

Quick note:  I did get the nVidia drivers working once under the -15 Ubuntu.  After restarting though, I'm back at square one.

Thanks for reading.

-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

AMD Athlon 64 3500+
nVidia 8600 GTS graphics card
3GB RAM
500 watt power supply
250 GB Maxtor HD

---

### Post by MasamuneX on 2007-10-13
Bump

Is there somewhere else I should post this?

---

### Post by hessiess on 2007-10-13
> -Why are there two choices for Ubuntu at GRUB?

most lickly becouse you have 2 kernals installed, i dont know about your outher problems, hav you tryed the gusty bata?

---

### Post by patrickfromspain on 2007-10-13
If you are using the nvidia drivers from the website, you must uninstall ubuntu-restricted-modules. Then you can install the nvidia drivers.

If you are using gutsy, you should install the nvidia-glx-new packages using synaptic, it's better and easier than using the nvidia's website ones.

---

