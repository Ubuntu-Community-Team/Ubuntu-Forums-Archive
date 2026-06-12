---
title: "Nvidia Woes"
date: 2008-08-05
forum: Hardware
---

### Post by Algo2 on 2008-08-05
I can't get nvidia to work, at least not well, no matter what I try.  In visa I get a super nice resolution 1280 x 800 (iirc).  It' sa 15.4" widescreen laptop.

So far with Ubuntu I have tried:

Compiling a new Nvidia driver from Nvidia.com (using sh Nvi....pkg2.run as root).  Now when I start up I get a prompt telling me it's in low graphic mode, a list of monitor options and video card options.  No matter what I do every time I restart it's t he same.  Max 800x600 resolution.

I tried a few other thin gs before that caused the screen to stay black, etc.

I'm at my wits end.  Any ideas?  I don't wanna go back to Vista.

---

### Post by Qchan on 2008-08-05
> **Algo2 said:**
> I can't get nvidia to work, at least not well, no matter what I try.  In visa I get a super nice resolution 1280 x 800 (iirc).  It' sa 15.4" widescreen laptop.

So far with Ubuntu I have tried:

Compiling a new Nvidia driver from Nvidia.com (using sh Nvi....pkg2.run as root).  Now when I start up I get a prompt telling me it's in low graphic mode, a list of monitor options and video card options.  No matter what I do every time I restart it's t he same.  Max 800x600 resolution.

I tried a few other thin gs before that caused the screen to stay black, etc.

I'm at my wits end.  Any ideas?  I don't wanna go back to Vista.

[b][color=darkred]
Have you tried something a bit easier?

You should isntall EnvyNG. It'll install your nVidia drivers automatically.
Click [here]("apt://EnvyNG") to install it.
[/b][/color]

---

### Post by phidia on 2008-08-05
Are you using Hardy, and did you try to enable the drivers for your video card by opening System > Admin > Hardware drivers?

---

### Post by phidia on 2008-08-05
I don't really have anything against envy, but Ubuntu is suppose to recognize the nvida card and give you an opportunity to enable the driver from the desktop. If Hardy is failing to do that it should get reported and fixed!

---

### Post by Qchan on 2008-08-05
> **phidia said:**
> Are you using Hardy, and did you try to enable the drivers for your video card by opening System > Admin > Hardware drivers?

[b][color=darkred]
I've used Hardy for 6 months. I've installed Ubuntu on many machines. I came across this issue once before. If you install Envy and run it, it'll uninstall what you already have and reinstall your nVidia drivers. After that, you shouldn't have any problems.
[/b][/color]

---

### Post by phidia on 2008-08-05
> **Qchan said:**
> [b][color=darkred]
I've used Hardy for 6 months. I've installed Ubuntu on many machines. I came across this issue once before. If you install Envy and run it, it'll uninstall what you already have and reinstall your nVidia drivers. After that, you shouldn't have any problems.
[/b][/color]

So you're saying Ubuntu should rely on a privately packaged fix > nvidia-envy is a privately packaged version of the NVidia driver by Alberto Milonerather than have the system work the way it's suppose to?

I'm asking this not just to be a PITA but because if people who have problems with the standard way of enabling the driver report it maybe the standard way would get fixed/work. 
It actually does seem to work in Intrepid (testing)-there seems to be some problem recognizing the nvidia card or just certain nvidia card models in Hardy.

---

### Post by Qchan on 2008-08-05
> **phidia said:**
> So you're saying Ubuntu should rely on a privately packaged fix rather than have the system work the way it's suppose to?

I'm asking this not just to be a PITA but because if people who have problems with the standard way of enabling the driver report it maybe the standard way would get fixed/work. 
It actually does seem to work in Intrepid (testing)-there seems to be some problem recognizing the nvidia card or just certain nvidia card models in Hardy.

[b][color=darkred]
Hey, a fix is a fix. Just because the plumber fixed the leak by using his son's playskool wrench, doesn't mean he shouldn't have.
[/b][/color]

---

### Post by doas777 on 2008-08-05
> **phidia said:**
> So you're saying Ubuntu should rely on a privately packaged fix rather than have the system work the way it's suppose to?

I'm asking this not just to be a PITA but because if people who have problems with the standard way of enabling the driver report it maybe the standard way would get fixed/work. 
It actually does seem to work in Intrepid (testing)-there seems to be some problem recognizing the nvidia card or just certain nvidia card models in Hardy.

I've had good luck thus far with the in-channel nvidia-glx-new. did you try enabling the restricted driver in your System -> Administration -> Hardware Driver's application?

---

### Post by Algo2 on 2008-08-05
I tried Envy.  Envy doesn't recognize my hardware.  I've downloaded a lot of restricted drivers from Synaptics.

I enabled hardware drivers, it made me have a black screen and I had to go into recovery mode to fix X.  Then I finally got a new Nvidia compiled.  That's where my low graphics mode is coming from.

---

### Post by doas777 on 2008-08-05
whats your xorg look like?

---

### Post by phidia on 2008-08-06
Algo2, If you're still having this problem (anyone with an 8 and maybe 9 series card that has this problem actually)
read [this thread]("http://ubuntuforums.org/showthread.php?t=881314") and get the runfile linked there. Really hope that helps.

---

### Post by hotweiss on 2008-08-06
1. sudo apt-get remove nvidia* (will also remove any other restricted modules (e.g.-madwifi), so watch out)
2. sudo apt-get install envyng-gtk
3. enable the proposed repositories
4. sudo apt-get update
5. sudo envyng -g
6. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
7. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by abhilashkumar on 2008-08-06
Nvidia for me worked out of the box by enabling restricted drivers from hardware manager. Once I enabled the restricted nvidia drivers, ubuntu downloaded the packages automatically and the display was fine. 

There is also the nvidia settings manager that you can use to tweak the display.

---

### Post by moon-light on 2008-08-06
[HOSTING]("http://www.methosting.com/"), [DOMAIN]("http://www.methosting.com/"),[WEB DESIGN]("http://www.methosting.com/"), [DATA CENTER]("http://www.methosting.com/"), [DEDICATED SERVER]("http://www.methosting.com/"), [LINUX HOSTING]("http://www.methosting.com/"), [WINDOWS HOSTING]("http://www.methosting.com/"), [RESELLER]("http://www.methosting.com/") 
[http://www.methosting.com/](http://www.methosting.com/)

---

### Post by Algo2 on 2008-08-06
Well it turns out that Ubuntu wasn't the problem.  The LCD went almost completely black (a tiny bit of image showing if you looked hard).  I think the nvidia chip was bad.  Anyways I took the compaq back to the store and got a Toshiba.  Hope this one works better :D

---

