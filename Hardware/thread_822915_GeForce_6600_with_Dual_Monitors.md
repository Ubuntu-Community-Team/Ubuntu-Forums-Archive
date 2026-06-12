---
title: "GeForce 6600 with Dual Monitors?"
date: 2008-06-08
forum: Hardware
---

### Post by sdlyr8 on 2008-06-08
I just installed a GeForce 6600 on my linux box running 7.10 Gutsy Gibbon. I'm wanting to set up dual monitors (both HP vs17). I've tried a few how-to's and none have resulted in anything! Every time I boot up after trying one of the methods it goes straight to saying the computer is running in low-graphics mode and its an 800x600 screen with both monitors having the same image. If anyone else has successfully set this up, can they give me some suggestions on how they got it to work?  Thanks!

---

### Post by Prospero2006 on 2008-06-08
Have you run the envyng driver installation program yet?

---

### Post by sdlyr8 on 2008-06-08
I tried.. with no avail! I have the repositories all enabled too.

> $ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk


Any reason why I'm getting this?

---

### Post by ad_267 on 2008-06-08
I have a 6600GT and setting up my dual monitors was fine. How are you trying to do it? I used the nvidia-settings tool and selected twinview when enabling the other monitor.

---

### Post by sdlyr8 on 2008-06-09
Actually it's weird. I've tried the nvidia-settings earlier and it kept coming up saying something like "No nvidia drivers found". Now I just ran it again and it opens but terminal is.. 
> ~$ sudo nvidia-settings 

ERROR: NV-CONTROL extension not found on this Display.

ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.

ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

i've attached the nvidia-bug-report.log file

The latest How-To i've followed is [http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

I'm stating to think it's just something with the driver not properly installed. Any way I can check if it's 100% functional?

[ATTACH]73429[/ATTACH]

---

### Post by sdlyr8 on 2008-06-09
Sorry.. Now it's attached!

[ATTACH]73428[/ATTACH]

---

