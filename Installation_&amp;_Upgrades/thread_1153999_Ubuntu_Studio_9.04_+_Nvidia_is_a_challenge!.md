---
title: "Ubuntu Studio 9.04 + Nvidia is a challenge!"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Darktrax on 2009-05-09
It is frustrating as hell! I have spent more than a day in a trial of Google researches, reboots, reconfigures, in every combination of careful work. Nothing succeeds. I conclude that I am just rubbish at it - or that maybe its just hard to do for anybody.
 
The provided Hardware Drivers installer fails, every time!

There is just no way to get a workable screen up with my monitor without editing /etc/X11/xorg.conf from within a working environment. Getting gdm to stop and stay stopped is not easy. "telinit 3" ,suggested by the Nvidia installer, will end up in with the x-server running and inviting a graphical login. Ctrl-Alt-Backspace will not kill the X-server.  

The "DKMS auto-installer" is seen to enter the attempt to complete the Nvidia-related module installation, but fails. In the end, I installed rcconf, and put a stop to it.

I can finally get a X desktop at 1600x1200 by completely replacing xorg.conf sections, and using the "nv" driver, which works every time, but of course does not offer 3D acceleration!

The handy "sgfxi" installer that works for other Debian distros is no use with Ubuntu.

All variants of "envyng" including the text-only envyng -t, and the GUI version envyng-qt do not succeed. All of thes installs end up with a required reboot, where the X-server fails to start, to run again if "nvidia" is replaced by "nv" on /etc/X11/xorg.conf.

Even removing, purging all nvidia-related stuff, ensuring the 2.6.28-3-rt kernel headers are installed, getting the Nvidia installer script correct for my (older) Nvidia GeForce FX 5700LE graphics card ( expects NVIDIA-Linux-x86-173.14.18-pkg0.run ) and starting from scratch, does not work. The installer gets through the compile, and then fails to install the module at the end. 

So - however much we all love Ubuntu, I begin to believe that it may not suit me. I do not give up easily, but this struggle to get to get to what I need is maybe more than I can manage. If any of you kind folk know of a really robust, uncompromising procedure that will achieve this - do tell.

---

### Post by jbeiter on 2009-05-09
I'm having the same problems, and have tried the same things. Hoping someone will respond to this thread...

---

### Post by Darktrax on 2009-05-11
There is a big thread now about installing the latest Nvidia drivers.
I **might** consider looking there, but, given that my Nvidia gfx card is not the latest and greatest, and  after all the effort put in, I also might just settle for what I managed in the end.

Nouveax! - the reverse engineered open source Nvidia driver that does not break the kernel every time you upgrade.

I used Synaptic to install it, and then I did  gksu gedit /etc/X11/xorg.conf
There, I simply replaced the device name "nvidia" with "nouveau"

It seems to work. The OpenGL applications run at apparently full speed, and the faint white-level noise patterning has nearly disappeared. Anyways, I am now too far into playing with the new audio toys and the real-time  kernel to care. :P

---

### Post by aaronlow on 2009-06-06
I had a similar problem with my setup, I have an AGP NVIDIA 6800 GT.  Upon installing Studio 9.04, the video would not come up.  I rebooted, and reinstalled several times before finding the solution.

1) go to a text login window (ctrl + alt + f1), login
2) type "sudo telinit 1"  -  this will get you to a state with no gdm
3) when I entered run mode 1, a text window appeared, asking me how I wanted to continue booting.  I chose xfix.  I am not sure what that did except create a nominally correct xorg.conf file.
3)  edit xorg.conf and replace any existing driver names with vesa, in the "Device" section.  My xorg file did not include any driver name, so I added [Driver      "vesa"] after the Identifier line (do not type the [ and ] characters.  Save and exit.  I used nano as the editor "sudo nano /etc/X11/xorg.conf"
4) type "sudo teleint 3"

my system then came up using the vesa drivers, where I could go into the hardware drivers and enable the nvidia-180 drivers

I hope this works for all of you.
Aaron Low

---

### Post by mey on 2009-06-08
Thank you aaronlow ! 
You are my saviour, I am new to linux and nearly gave up on it before even starting... talk about user friendly!!! Your solution should be a "sticky note" or something directly on the ubuntu studio website i.e. Warning Nivdia Graphics cards !

Let's hope its worth it, apparently the video editing is great and after all I want to get away from windows ):P

... so let the adventure begin ...

PS to get to a text login I had to use the safe mode from the boot menu

---

### Post by mey on 2009-06-08
errr well actually if you tell me where to find instructions for gettting "into the hardware drivers and enable the nvidia-180 drivers" that would get me started off in the right direction lol

thanks

... actually I just found it... you just click on the icon next to the date on the top left hand part of the screen... let's hope all linux is that easy ;)

---

