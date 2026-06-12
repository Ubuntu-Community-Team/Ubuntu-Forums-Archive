---
title: "Nvidia GeForce2 GTS/Pro AGP"
date: 2011-11-16
forum: Hardware
---

### Post by TecXero on 2011-11-16
I have only the slightest clue what I'm doing. I'm using an older Desktop (82845G Intel chipset, 2.4ghz Pentium 4 CPU-32bit, 2gb ram, etc) with Ubuntu 11.10.

I've been trying to get it to use a driver for my video card (Nvidia GeForce2 GTS/Pro) which, since my motherboard only has an AGP and PCI slots, that's what I'm stuck with.

I did the standard Terminal install:

sudo apt-get install nvidia-current

the nvidia tool told me to run nvidia-xconfig and restart. When I did it would freeze on the Ubuntu startup splash. After trying to find a solution to no avail I did a fresh install from my USB drive to be able to get past the splash.

I then tried to download the legacy driver from Nvidia (Linux Display Driver Version 71.86.1) and when I ran it using:

sudo sh /home/(username)/Downloads/NVIDIA-Linux-x86-71.86.15-pkg1.run

after going through it for a bit it says I need to shut down X. I then run:

sudo service lightdm stop

I then try to run the .run pack again but it won't respond. I assume I did something completely wrong, like I said I'm new to Linux. Was hoping someone here would be able to help with coming up with a non-costly solution, preferably just getting a driver running for my current video card. If there is no solution then it's not that big a deal. Ubuntu seems to run without the driver well enough, just nothing too graphic intensive, and I only need this desktop to last me through the rest of College.

---

### Post by TecXero on 2011-11-16
UPDATE: Got it installed (didn't know I had to hit CTRL+ALT+F1 to bring up the prompt). It said it had to disable nouveau and it did. Said I have to setup the xorg.conf file. I screwed around with it for a while (backed it up of course) and I can't get anywhere with it. Currently I'm stuck in 1024x768 resolution with no hardware acceleration. Additional Drivers says the driver is installed and running, but System Info says it's unknown. The Nvidia X server doesn't really give me anything option wise.

I assume it just all comes back to getting the xorg file setup right, any help there would be great.

---

