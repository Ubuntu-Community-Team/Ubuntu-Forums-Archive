---
title: "Display Nightmares"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by doveman on 2008-12-18
I've just done a fresh install of Ubuntu 8.10. I had a couple of problems on the first two attempts, which were probably due to certain LVM partitions not being large enough but after resizing (if I recall correctly) /opt and /usr, the third attempt went fine (is there anywhere that explains the minimum space Ubuntu needs in the various directories to install successfully?)

That was nothing compared to what I had to deal with once the install had finished. First, I'm confronted with a mass of unintelligible colour instead of a desktop. I Ctrl-Alt-F2 to a terminal window, only to find that the cursor marker's stuck in the top left (not that anything I type appears there) but the main problem is that once the screen is full, it refuses to refresh or display any output without me switching away to another terminal window and back again.

I reboot and use the vga= switch, which gives me a recognisable desktop but no mouse cursor (which makes it impossible to use) and I still had the same problems with terminal windows.

xorgconfig, randr and displayconfig-gtk all seem to be absent. Eventually, I use "sudo dpkg-reconfigure xserver-xorg", which only asks me one question about graphics, referring to the framebuffer, but after trying it enabled and then disabled, I manage to get a usable desktop and run Nvidia config, which tells me to run nvidia-xconfig, which modifies xconf and results in a usable OS.

I'm running an Nvidia FX5600 GPU and Dell D1226H monitor, so nothing particularly exotic. I'm surprised and disappointed, considering that Ubuntu is touted as one of the more user-friendly distros, that I had this much trouble. It actually reminded me why I'd not got far with Linux in the past, as I'd experienced the corrupted desktop with a LiveCD (I think it was a Ubuntu/Kubuntu disc) and given up.

If there's anything I can do to help track down why this happens, I'd be glad to help in the hope that someone else might not have to experience this and be put off Linux for life. I've got an Xorg.0.log with a lot of display related errors in it that might make sense to someone.

---

### Post by wpshooter on 2008-12-18
Are you installing this on a computer that is running another O/S, such as M/S windows ?

---

### Post by albinootje on 2008-12-18
> **doveman said:**
> 
I'm running an Nvidia FX5600 GPU and Dell D1226H monitor, so nothing particularly exotic. I'm surprised and disappointed, considering that Ubuntu is touted as one of the more user-friendly distros, that I had this much trouble. It actually reminded me why I'd not got far with Linux in the past, as I'd experienced the corrupted desktop with a LiveCD (I think it was a Ubuntu/Kubuntu disc) and given up.


I think Linux cannot be compared with Apple or SUN MicroSystems.

Apple and SUN both have the big advantage that they both produce the software and hardware. 
(In SUN's case i mean of course SUN hardware, and not the i386-family :)

Microsoft also has the advantage that it has loads of cash, and good contacts with hardware-suppliers. And several hardware-suppliers use a Microsoft-compiler to compile the software for the BIOS, which also gives MS an advantage in fixing (or work-around) certain problems.

The Linux-developers are in a different situation, and it's nice that Nvidia is a company which is willing to open up a bit towards Linux, but it's far from an ideal situation for Linux in general.

> 
If there's anything I can do to help track down why this happens, I'd be glad to help in the hope that someone else might not have to experience this and be put off Linux for life. I've got an Xorg.0.log with a lot of display related errors in it that might make sense to someone.

Check [http://launchpad.net/](http://launchpad.net/) and file a bug-report mentioning the problem, your video-card, computer brand + type, lspci output, your X log-file and whatever more is needed.

---

### Post by doveman on 2008-12-18
> **wpshooter said:**
> Are you installing this on a computer that is running another O/S, such as M/S windows ?

Yeah. I've got two XP installs, each in their own primary partition. The Ubuntu install is completely in the extended partition, with separate logical partitions for /, /boot and swap and the rest in the LVM volume.

---

### Post by doveman on 2008-12-18
> **albinootje said:**
> Check [http://launchpad.net/](http://launchpad.net/) and file a bug-report mentioning the problem, your video-card, computer brand + type, lspci output, your X log-file and whatever more is needed.

Thanks. I'll do that.

---

