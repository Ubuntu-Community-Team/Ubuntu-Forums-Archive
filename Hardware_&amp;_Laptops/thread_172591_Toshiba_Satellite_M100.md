---
title: "Toshiba Satellite M100"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by muadib on 2006-05-08
I am running Ubuntu Dapper on a Toshiba Satellite M100 and am unable to get accelerated xorg, wireless to work or suspend to work properly.

With accelerated xorg, I have tried to use Xorg's i810 driver but glxinfo reports "direct rendering no".

ACPI reports to be working but when I hit the suspend button I'm not sure how to bring the computer back without powering down and rebooting.

If anyone has had success with this laptop and these 3 components I would be interested to know how to get this hardware working on my computer.

Mathieu

---

### Post by Tom Tiger on 2006-05-09
I'm not sure if you have to set the powerup mode in the bios on Resume

In theory it should work.

---

### Post by pinballkid on 2006-05-09
I can confirm that I'm also having trouble with this laptop. In fact, I've just downloaded and installed a fresh dapper it fails on starting X, giving this:

Fatal server error:
no screens found

Is this a problem with the nvidia driver for this card?

---

### Post by pinballkid on 2006-05-09
I've found that changing your /etc/X11/xorg.conf to use the 'vesa' driver at least gets me into Gnome :)

there's more on that in this thread: [http://www.ubuntuforums.org/showthread.php?t=148517](http://www.ubuntuforums.org/showthread.php?t=148517)

---

### Post by muadib on 2006-05-09
As far as I know, the laptop uses an integrated intel video card:

--
VIDEO CARD TYPE  	

Intel® Graphics Media Accelerator 900 (945GM) with up to 128MB shared video memory (UMA) 
--
from:
[http://www.cybershop.net.au/Notebooks/ToshibaSatelliteM100.shtml](http://www.cybershop.net.au/Notebooks/ToshibaSatelliteM100.shtml)

However, using the i810 driver for xorg has not given me accelerated video.

Mathieu

---

### Post by fabrice on 2006-05-19
Hello, 
I've just got a Toshiba M100-JG2 which has Intel 945GM graphics. 
I've tried to boot on the Live CD (5.10), and X failed to launch. I assume this is because there is no driver for the 945GM on the Live CD. 
Actually I wanted to test Ubuntu before installing a "regular" version on my hdd. 
Does the (wired) LAN work out of the box ? 
How about the wi-fi ?

Btw, what is the space requirement to install Ubuntu ? A quick browse through the forums shows there doesn't seem to be a consensus. Somewhere around 2GB seems to be ok for a comfortable installation. I reserved 10GB on my laptop. I assume this should be enough, right ?

---

### Post by Mikecore on 2006-05-21
I have a Toshiba Satellite M55 not the same I know but bear with me I do have the Intel I915 video card. Try booting ubuntu with "acpi=off" and use the I810 driver.  Your 
video should work fine.

---

### Post by sunset_studies on 2006-06-14
deleted

---

### Post by sunset_studies on 2006-06-14
deleted

---

### Post by sunset_studies on 2006-06-14
deleted

---

### Post by sunset_studies on 2006-06-14
First: can an admin please delete those last posts? I kept using 'reply' thinking it was 'edit' 


Running Dapper final on a Toshiba Satellite M100 here and the issues you raised in the original post all seem to have been addressed (just in case anybody was wondering...).

One thing I haven't got working yet is the remote control. There must be some sort of Linux support available for this remote as the 'Express Media Player' that comes with this laptop is actually a stripped down Linux distro, and it's controllable via the remote. Has anybody here got it working under Ubuntu?


Can't think of anything else that's not working (but I've not tested everything, e.g., wireless).

Edit: can/should this be moved to another forum?

---

