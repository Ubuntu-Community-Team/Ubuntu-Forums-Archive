---
title: "new graphics card"
date: 2010-11-09
forum: Hardware
---

### Post by Richardarkless on 2010-11-09
Hi my previous graphics was an integrated geforce 7050, anyway I decided about a week or so ago to upgrade to a zotac geforce 210, anyway received it today, I plugged it in and it went straight to the command line so xorg couldnt start

the error I was receiving was nvidia module failed to load then after it driver not found

So far I have tried

manually starting it (sudo startx)

reconfiguring xserver-xorg (sudo dpkg-reconfigure xserver-xorg)

removing the nvidia-current package and its nvidia-settings and then installing them again

removing xorg.conf

All these seem to not work for me

Please help

---

### Post by ellgor on 2010-11-09
Hi,

Go to the nvidia site and get the latest driver for your card, keep the download in a handy location, /home

Open a terminal and stop the gdm(GraphicDisplayManager) with:

sudo gdm-stop

A black screen will be presented with terminal access, type in:

telinit 3

another black screen will be presented,now cd to the downloaded driver and start it like this:

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

 Follow the onscreen guide from Nvidia and when done

 Start GDM

sudo service gdm start
 
Regards, Ellgor.

---

### Post by Richardarkless on 2010-11-09
> **ellgor said:**
> Hi,

Go to the nvidia site and get the latest driver for your card, keep the download in a handy location, /home

Open a terminal and stop the gdm(GraphicDisplayManager) with:

sudo gdm-stop

A black screen will be presented with terminal access, type in:

telinit 3

another black screen will be presented,now cd to the downloaded driver and start it like this:

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

 Follow the onscreen guide from Nvidia and when done

 Start GDM

sudo service gdm start
 
Regards, Ellgor.

right ive downloaded and when I run it, it gets to building kernel module then an error saying that it is unable to load the kernel module nvidia.ko because gcc differs from the one used to build the target kernel

I also installed build-essentials before running the above

I got the nvidia driver version 260.19.12, how does this differ from installing using nvidia-current, both are version 260

---

### Post by Richardarkless on 2010-11-09
Just an update

whenever I install or boot windows 7 with the graphics card in, it bluescreens

When it isnt it installs or boots fine, so is it the graphics card which is the problem?

I also booted off a ubuntu live cd and it wont go any higher than 640x480 on vga and 1024x768 on dvi

Isnt the nouvea drivers suppose to render the gui at max resolution for that monitor ?

---

### Post by MZ250Supa5 on 2010-11-10
I tried the above command only to get:

sudo: gdm-stop: command not found

I'm trying to upgrade to the 260.19.12 driver so that I cna run my GTS 450 graphics card properly as I keep getting messages that my graphics capabilities are inadequate to run even Second Life with the driver that's available from the repository.

---

### Post by ellgor on 2010-11-10
Hi,

To Richardarkless

You don't say if the nouveau drivers are in use, I'll presume they are, load in any of the nvidia drivers from the repos (synaptic) this will disable them as they wont go without a fight, then go through the procedure as first given.

To MZ250Supa5

I have come across that message before, not sure of the cause, look around at "command not found" in the forums.

Regards, Ellgor.

---

### Post by efflandt on 2010-11-10
RichardDarkless, did you disable your integrated video (if possible) in BIOS (CMOS setup from BIOS splash screen before any OS boots)?  Or maybe that used one of the older nvidia driver versions (185 or 173) which does not work with the new card.  If you boot with just the integrated video, what shows for NVIDIA Driver Version in NVIDIA X Server Settings?

Try using System > Adminstration > Additional Drivers to "remove" the nvidia that it used so the system will fall back to nouveau, shut down.  Reboot with the new card installed, disable on-board video if possible, and boot to Ubuntu.

If you want to get 260.19.12 drivers instead of default 260.19.06, you have to add x-swat to your repositories:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update
```Then go to System > Adminstration > Additional drivers, "activate" nvidia and reboot.

I have GT 220 which worked fine with 256.53 drivers (which was slow for some other nvidia cards) in 10.10 beta, worked fine with current 260.19.06 (faster despite flood of meaningless errors in logs), and works fine with 260.19.12 (fast with no log errors).  The splash screen may end up looking sort of crappy (text Ubuntu and dots), but X graphics works great.  I have used DVI to HDMI and am currently using HDMI for 1080p HDTV.

I got HDMI sound working too, while still being able to switch to my analog 2.1 speakers.

---

