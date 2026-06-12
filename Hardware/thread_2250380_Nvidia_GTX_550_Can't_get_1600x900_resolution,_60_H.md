---
title: "Nvidia GTX 550: Can't get 1600x900 resolution, 60 Hz refresh rate"
date: 2014-10-28
forum: Hardware
---

### Post by ubuserone on 2014-10-28
Currently on GTX 550 ti but I tried various way for Months and I still can't get it work with 1600x900 with 60 refresh rate .
I suspect it was cause by the graphic driver on ubuntu.

Should I change to Ati for better support resolution ? any user using 1600x900 resolution ? what graphic card currently on use ?

---

### Post by MartyBuntu on 2014-10-28
Which driver are you using?

---

### Post by ubuserone on 2014-10-29
> **MartyBuntu said:**
> Which driver are you using?

Tested with Nvidia GF116 version 331.38 from nvidia-331 and X.org server  - Nouveau ( 14.04 64bit)
With custom resolution seeting via xrandr does not support 1600x900 refresh rate at 60hz.

After Install 14.04 with latest updates having the same issue on custom resolution and I suspect it's cause by the driver it self since I tested installing windows 7 , I can do 1600 by 900 with 60hz refresh rate.
[http://ubuntuforums.org/showthread.php?t=2249608](http://ubuntuforums.org/showthread.php?t=2249608)

Was started this old thread months ago , though of the cause of old driver 12.04 causing the issue 
[http://ubuntuforums.org/showthread.php?t=2222657](http://ubuntuforums.org/showthread.php?t=2222657)

What would have been the cause of it ?
All my log is at this thread [http://ubuntuforums.org/showthread.php?t=2249608](http://ubuntuforums.org/showthread.php?t=2249608) 

Thank you MartyBuntu , hope there's a fix for it.Not everyone vision is clear , some are long sightedness on 1920x1080 especially for elder people.1600x900 is much larger and easier.

---

### Post by MartyBuntu on 2014-10-29
You have an NVIDIA GTX 550-Ti?

What display screen, make and model?

---

### Post by ubuserone on 2014-10-30
> **MartyBuntu said:**
> You have an NVIDIA GTX 550-Ti?

What display screen, make and model?
At my log [http://ubuntuforums.org/showthread.php?t=2249608](http://ubuntuforums.org/showthread.php?t=2249608) using Dell 2312hm [http://ubuntuforums.org/showthread.php?t=2250377](http://ubuntuforums.org/showthread.php?t=2250377)

It really gets blur on 1600x900 , with numerous tried i still can't get it to run at 60hz.

---

### Post by ubuserone on 2014-11-04
How many of you guys using nvidia graphic card ? 
Should I directly install driver nvidia driver from the nvidia website ?

---

### Post by ubuserone on 2014-11-08
bump for today :)
Request for member to test of custom 1600x900 resolution

---

### Post by ubuserone on 2014-12-10
Bump , Request again if someone have this card

---

### Post by kjh_ngisd on 2014-12-26
> **ubuserone said:**
> Bump , Request again if someone have this card

Hi ubuserone. 
I'm sorry to say that I have the same issue. 
I'm currently set to boot to either Ubuntu 12.04, Ubuntu 14.04 or Windows7. And I'm using NVIDIA's GT555M on my Dell XPS17 laptop.

In 12.04, I'm using the Nouveau drivers and can get 1600x900. 
On Win7, I get 1600x900

On Ubuntu 14.04, I can't get more than 1024x768. I've tried both Nouveau and NVIDIA's drivers without success. Also, I can't seem to engage the NVIDIA chip at all -- I can get the INTEL one to render at 60FPS (or something) but can't get the NVIDIA GPU to reliably produce anything. (Occasionally, I can get it to fire at 1200FPS until I reboot, then it switches back. And even then, it doesn't work properly).

(I'm guessing you knew that the card has 2 chips -- one Intel and one NVidia). 

I've basically given up for now. I'm hoping that Ubuntu 15.04 is better. Or maybe the new NVIDIA drivers will work? 
I suspect it's some issue with drivers failing to interact with the new kernal. Sadly, the latest NVIDIA drivers don't work ; I've tried version 340.65 -- which is their newest, I think -- but no luck.

I've logged a couple bugs with NVIDIA and had a few chats with their tech support, but nothing has worked. 

One thing I can recommend to try is that on your computer somewhere, if you have installed NVIDIA's drivers, you should have a script called "nvidia-bug-report.sh" that collects all the video information and logs a bug report with NVIDIA. They were responsive, but not helpful for me, but you may have better luck?

If you learn anything, let me know. 

Here's one of my threads asking for help, along with some of the things I have tried:

[http://askubuntu.com/questions/497867/nvidia-prime-with-14-04-problems](http://askubuntu.com/questions/497867/nvidia-prime-with-14-04-problems)

I've been more focused on getting the NVIDIA GPU engaged than getting the graphics resouktion to 1600x900, but I think the issue is the same. Anyway, please poke me if learn anything. And I'll update one of our posts if I do. 
--kevin

---

### Post by pqwoerituytrueiwoq on 2014-12-26
I have used a 550 TI on a 1600x900 HP monitor without issue, i cant test it currently as a sold the card and my dad has the monitor
can you post the output of [FONT=courier new]xrandr -q[/FONT] your issue is probably with the monitors edid

@kjh_ngisd
you have a very different issue, OP does not have hybrid graphics your best best is the latest drivers in the xorg edgers ppa and installing bumblebee
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

