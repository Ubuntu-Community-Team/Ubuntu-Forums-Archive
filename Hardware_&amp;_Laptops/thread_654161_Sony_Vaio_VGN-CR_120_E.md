---
title: "Sony Vaio VGN-CR 120 E"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by OrionFyre on 2007-12-30
Allow myself to introduce... uhh... myself...

Sony Vaio VGN-CR120E laptop with Ubuntu 7.10 Gutsy Gibbon

Please let me make clear I am not in any way knowledgeable about Linux or its inner workings, I am still very NooB to the whole thing. I cannot go into technical details about why the problems exist, or how the solutions work, only that they got things working the way they *should*. I am creating this topic for an easy reference for someone who might have similar hardware (or the same model) or issues so they can have a one-stop shopping experience for trouble shooting.

It should be noted that I was very impressed with how well Linux worked “out of the box” on this system with such little tweaking on my part as you can see below.

The document will be succinct, pithy, and lacking in technical descriptions. I will update this post with additions as I go along.

-----------------------------------------------------

[SIZE="5"]_Sound:_[/SIZE]
**Problem:** I get no sound until I plug in headphones. After which sound continues to work properly whether headphones are plugged in or not.
**Solution:** Thanks to murmel in his post for this solution!
```
sudo nano /etc/modprobe.d/alsa-base
```
at the bottom add the following line
```
options snd-hda-intel model=vaio
```

The last step was this apt-get:
```
sudo apt-get install linux-backports-modules-$(uname -r)
```
Following a reboot the system greeted me with the pleasant sound of the Ubuntu drums at the login screen. No more headphones required to get sound working after each boot.

-----------------------------------------------------

[SIZE="5"]_Webcam:_[/SIZE]
**Problem:** Webcam fails to load proper drivers and is not recognized, no video0 or video1 device
**Solution:** is currently a work in progress.
lsusb reveals
```
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
```
Once again murmel has been the source of any progress thus far, thanks murmel!

-----------------------------------------------------

[SIZE="5"]_Compiz-fusion:_[/SIZE]
**Problem:** Compiz fails to load based on a blacklisted id.
**Solution:** Compiz worked reasonably well with the skip checks option set to yes. some things are glitchy like shadows and transparencies, but are survivable if left on, or can be shut off.
```
SKIP_CHECKS=yes compiz --replace
```
**Additional note:** the skip checks was necessary as compiz would not load because of the blacklisted device, however in the process of creating this post I have noticed that I no longer need to use the SKIP_CHECKS. To my knowledge the only thing I can come up with is that I have since installed xgl. I cannot determine if this is the reason for no longer needing the SKIP. I have yet to configure compiz to automatically start so that I can conserve battery power when no outlets are available.

-----------------------------------------------------

[SIZE="5"]_Hibernate/Suspend:_[/SIZE]
**Problem:** Hibernate and Suspend do not work properly.
**Solution:** Work in progress! I have little need as of yet for these features so my investigation into a solution is slow in coming.

-----------------------------------------------------

---

### Post by cimnik on 2008-01-10
I have the CR220E and these instructions are applicable as well. I had learned all this myself prior, however, this post would have been useful when I got the laptop new.

Some additional notes:
[LIST]Only installing the back ports for the sound drivers seem to be necessary. (Its all I did!)[/LIST]
[LIST]Compiz-fusion likely, after the first run, created a config file (~/.config/compiz/compiz-manager) which contains SKIP_CHECKS=yes. I, instead created said file with said contents to get it working.[/LIST]
[LIST]Forcing compiz to work, however, causes totem/gstreamer and vlc (only two I tested) to fail to render video. Problem lies with incompatibilities with XVideo which is the default for video output. I changed it to just use X11. I don't know of any other solution.[/LIST]
[LIST]Also, direct rendering is not on. Claims its indirect. I have to drop to the vesa drivers to play Roller Coaster Tycoon. Unfortunate because I use avant-window-manager and thus lose my dock. With the intel drivers, anything graphical/DirectX in wine kills X.[/LIST]
[LIST]Webcam lacks drivers outright. Motion Eye is very propriatary if I recall correctly and drivers need to be reverse engineered.[/LIST]
[LIST]I noticed if a wireless connection is dropped from the router, the wireless drivers get stuck and won't connect to anything else. Solution is to restart to to rmmod/modprobe the iwl4965 module.[/LIST]
[LIST]Screen brightness buttons on laptop don't work. At least the Gnome brightness applet does work. I believe this one is a known bug.[/LIST]

My hope is that the suspend and hibernate will be fixed by Hardy Heron, as the problem could be the hardware is just too new for Gutsy kernel...

---

### Post by PizzashaX on 2008-03-04
Hi, I just got my distro of Ubuntu in the mail.
It is 7.10.
I have a slight problem with trying to boot it.

After I put in the CD I go to the first option. So then I get the loading bar, after that I get a bunch of weird lines on my screen and nothing happens then. 

Can anyone help out?

---

### Post by mixandgo on 2008-03-14
webcam works (vgn-220e) with the r5u870 driver and suspend also by removing the uvcvideo module

---

