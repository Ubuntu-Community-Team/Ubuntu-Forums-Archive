---
title: "Using my LCD TV with Ubuntu"
date: 2008-09-28
forum: Hardware
---

### Post by cu55ter on 2008-09-28
Hi Can anyone help please Im new to Ubuntu and I've just bought a bare bone Pundit-r to use as a media center in my living room, I've installed Ubuntu 8.04 LTS. My motherboard has an integrated ATI radeon 9100 graphics card but I've had a bad time trying to get my Philips 37" lcd tv to display anyting. So I've gone out today and bought an Nvida Tornado GeForce FX 5200 gapics card but it seems I'm having the same problem. Can anyone help me to get ubuntu to work on my lcd tv?? Thanks Tony

---

### Post by phidia on 2008-09-28
There is a thread [here]("http://ubuntuforums.org/showthread.php?t=821875&highlight=Philips+lcd+tv") on phillip's HDTV but it isn't very helpful.
You will probably want to use xvidtune and also find out what the exact modelines are for your TV. Searching the model # and using and online modeline generator could help too.

What errors are you getting when the xserver tries to start? That's something you can post here and/or search.

---

### Post by cu55ter on 2008-09-29
yeh sorry I should have said my lcd tv is a philipps 37PFL5522D supported PC resolution 
640 x 480, 60/ 72/ 75/ 85 Hz
800 x 600, 72/ 75/ 85 Hz 
1024 x 768, 60/ 70/ 75/ 85 Hz

At the moment I have a monitor connected to the pc as well thats how I can see what I'm doing I initially tried to install Ubuntu I had the LCD tv pluged into the pc via the dvi cable and the monitor through the vga connection but for some reason the system crashed and I installed it again but this time I removed the LCD tv and it installed fine but I get a message video not supported and cant see anything on the lcd when its plugged in and nvidia drivers installed in hardware drivers and enabled.

any help would be appreciated.

Tony

---

### Post by phidia on 2008-09-29
Have you tried to open a command line by pressing Alt+Ctrl+F1?
Do that and at the command line (CLI) try this command > sudo dpkg-reconfigure -phigh xserver-xorg

Getting a screen without any overlap-that is getting x to support your TV modelines can take some work. If the dpkg command doesn't work you may need to edit your etc/X11/xorg.conf. 

You can experiment with different modelines but be sure you know what your TV is capable of. SInce you have supplied some resolutions you can check your xorg.conf and make sure those are listed.

---

