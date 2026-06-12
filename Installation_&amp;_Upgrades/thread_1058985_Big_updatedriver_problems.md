---
title: "Big update/driver problems"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by metalhead656 on 2009-02-03
Hello everyone

First off I'm running Ubuntu 8.10 on a Dell Latitude D620 laptop.

Everything was working gloriously until I tried to update my nvidia graphics card driver from the 173 version to the 180 version. When I tried initially doing this the computer needed somewhere around 723 new updates so I went ahead and installed them altogether. From what I can understand it was a new Kernel for Ubuntu (or I could be wrong)

After the update I tried rebooting my computer and I received a number of errors which were too many to list...then I rebooted again and I was able to get where I am now. I have everything working exactly as before except for the things listed below. 

1. Compiz fusion no longer works, even though the settings are all fine (they're actually exactly how I left them before the update)

2. I no longer have ANY drivers when I go to system -> administration -> hardware drivers...and when I try to download anything (from synaptic package manager) I get:

vidia-glx-177-dev:
 Depends: nvidia-glx-177 but it is not going to be installed

Also, this for more than just that one driver, its for all the graphics cards I get the same response. But I managed later on to download the supposed drivers I need (96,173,177...) but it doesn't matter none of them will install. 

3. My wireless card no longer works (ipw3945), but my wired connections still work (it even still shows the network connections I was connected to in the past, but just refuses to scan for them)

4. Wine works up with any game but runs terribly slow (probably because I can't enable 3D acceleration or anything of that matter)

Things that I have tried and DON'T WORK

1. removing the nvidia 180 molaises (spelt something like that...sorry) driver and attempting to reinstall other drivers...it says that I have installed them but I still get an empty hardware drive list...fail

2. reinstalling the wireless driver...fail

3. searching for a flaw in my compiz settings...no flaw...fail

I feel as if once I get my drivers working back up again everything should be fine...

Is there any way to reverse an update?

It almost feels like when I first installed Ubuntu and it had no drivers...except now I lost the ability to install them.

Please let me know if there's anything I can do..I really don't want to have to do a full re-install of everything. Any help would be greatly appreciated.

---

### Post by battleshipbadger on 2009-02-03
join the club, mate.  i lost my dvd-+rw drivers and sound card drivers.

---

### Post by metalhead656 on 2009-02-03
yeah I gave up already and just re-installed Ubuntu....I couldn't even log back in to my computer after I shut it down after that...its a shame..I wish there was a better recovery system

---

### Post by geroad on 2009-02-10
> **metalhead656 said:**
> yeah I gave up already and just re-installed Ubuntu....I couldn't even log back in to my computer after I shut it down after that...its a shame..I wish there was a better recovery system
did you try this (run in terminal in 8.10)

sudo apt-get install linux-backports-modules-intrepid

It installs linux versions of some drivers. It restored my driver for the wireless card.
( Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter )

---

### Post by jimv on 2009-02-10
Best thing to do is go here and get the driver:

[http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-Linux-x86-180.22-pkg1.run)

And then drop to a terminal by pressing control+alt+f1 and running these commands:

sudo /etc/init.d/gdm stop
sudo sh (wherever you saved that file to)

Then reboot (Type 'sudo reboot').

---

