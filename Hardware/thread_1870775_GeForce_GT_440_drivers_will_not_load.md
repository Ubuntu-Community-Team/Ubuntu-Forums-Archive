---
title: "GeForce GT 440 drivers will not load"
date: 2011-10-27
forum: Hardware
---

### Post by DarkDancer on 2011-10-27
I got myself a brand new GeForce GT 440 card today (UPS, got it from NewEgg) and put it into my computer. I am using 11.10 with Unity. Well, the computer boots ok, and looks all right, I have been to ccsm and enabled the Unity plug in but the changes I make to it do not actually work. Not really surprised by that because I do not have the drivers loaded. When I go however to the Additional Drivers screen, it does she me 2 drivers there, NVIDIA accelerated graphics (version current) [Recommended] and the post-release update version. If I try to Activate either I get:

"Sorry, installation of this driver failed."
"Please have a look at the log file for details: /var/log/jockey.log"

Jockey.log says

> 2011-10-27 20:56:15,083 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-27 20:56:15,095 ERROR: xorg:nvidia_current: get_alternative_by_name(nvidia-current) returned nothing
2011-10-27 20:56:15,174 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/nvidia-173-updates/alt_ld.so.conf
2011-10-27 20:56:15,174 DEBUG: nvidia_current is not the alternative in use

Help please! ;)

---

### Post by DarkDancer on 2011-10-28
Bumpity bump bump....

---

### Post by DarkDancer on 2011-10-29
Wow, cool, stumped you all! ;)

---

### Post by DarkDancer on 2011-10-30
Ha! Got it fixed without you. Did This:

> $ cd /var/lib/apt
$ sudo mv lists lists.old
$ sudo mkdir -p lists/partial
$ sudo apt-get update

Then this:

> # sudo -s -H
# apt-get clean
# rm /var/lib/apt/lists/*
# rm /var/lib/apt/lists/partial/*
# apt-get clean
# apt-get update 

Why did this work? No clue, was trying to solve something else (trying to insall Chrome but was getting an untrusted error, that still does not work btw) but just gave it a shot and weeeeee, the drivers loaded after that.

---

### Post by oedsrm on 2011-11-13
Unfortunately DarkDancers solution did not work for me.  I have a fresh Oneric install on a dell vostro 3400.

Thanks anyway.

---

### Post by oedsrm on 2011-11-13
Hmm...my drivers installed after the following steps... I'm not sure if DarkDancers steps helped...

[LIST=1]
[*]Install synaptic package manager
[*]Reload all packages
[*]Reinstall the nvidia-current package
[*]Reboot for good measure
[/LIST]
I noticed the driver is quite large and takes a while to download.  Longer to download than it took for the 'jockey.log' error message to appear.  Perhaps a timeout is affecting things?

This reinstalling approach also helped with broadcom wireless drivers (bcmwl-kernel-source package to be precise).

---

