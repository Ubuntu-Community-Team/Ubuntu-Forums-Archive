---
title: "Shutting down issue with ATI Mobility Radeon 4500"
date: 2012-11-04
forum: Hardware
---

### Post by lz1dsb on 2012-11-04
I recently upgraded to Ubuntu 12.04 from 11.10. And after having some issues with the desktop, I installed the fglrx driver for my video card. The one that's distributed with the Additional Drivers app in Ubuntu. Here's what I have:
lspci | grep ATI

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series]

fglrxinfo

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.11627 Compatibility Profile Context

From time to time when I'm shutting down the system hangs and I've got an error message regarding the fglrx driver (I've disabled the splash screen for the shutting down so that I could see what's going on). Unfortunately I can't copy the message as at the moment it's outputted I can't do anything, but just watching it :confused: At the end, the only way to shut down they system, is to use the power button. And off course the next time I power up my laptop, the system has to clean up the journal. 
I'm thinking about using the official ATI Catalyst driver, version 12.6... as my video card is now considered legacy, according to ATI :P 
Has anyone used it? Could you share your experience with it? I really hope that this could solve the shutdown problem I have...

---

### Post by lz1dsb on 2012-12-03
Below is a picture of the error I've got from time to time when I shutdown my laptop. It's clear that I have an issue with the fglrx driver, but how to fix it? I'm also running the latest kernel update for Ubvuntu 12.04. An still the problem persists...

---

### Post by lz1dsb on 2012-12-03
If anyone could give me an idea how I could get this error output logged I would be grateful. I know that the picture sucks, but that's the only way I could capture the error...

---

### Post by Portaro on 2012-12-03
I thinking your problem is not a big problem, i understand your only problem is that fglrx ahve some problem to show plymouth image, plymouth is an image graphic program to show anything when you boot pc and shutdown.

In your case the problem is more curious that i see and experiment in my ubuntus, nromally for me i dont have the plymouth image in the boot of system or have only text plymouth .

Maybe you can solve your problem install this 
sudo apt-get install v86d [v86d info here- [http://packages.ubuntu.com/lucid/v86d]](http://packages.ubuntu.com/lucid/v86d])

then 

sudo update-initramfs -u

 sudo update-grub2

After this reboot pc and see if you have an image on the shutdown - if you 
not have the image read this to obtain more info about .
uvesafb mode_option

---

### Post by lz1dsb on 2012-12-07
Dear Portaro, 
Thank you for giving me this suggestion. Usually very few people write to my threads :lolflag:
Anyway. The main issue for me is that the file system isn't properly unmounted during the shutdown process, so each time the journal has to be replayed. And I'm worried that if I do this too often it will brake the file system at some point. 
I have also disabled the Splash screens both for booting up and shutting down. This is how I saw that the system hangs at this particular error.
I have to check on that package you suggest...

---

### Post by lz1dsb on 2012-12-08
I was able to catch a more clear picture of the same error while shutting down. It looks like each time the error is exactly the same.

---

### Post by lz1dsb on 2012-12-21
I found that when I use Unity 2D instead of the default UI Unity 3D, I don't have that issue. I've done a few restarts and shutdowns but so far it doesn't show up. 
Hm... If this is the case, I'll even put Unity 2D as a default UI... I don't care about eye candy that much nowadays :p

---

### Post by lz1dsb on 2013-01-03
i have been using my laptop with Unity 2D for quite some time now. There is no issue when I shutdown the laptop. I don't mind the lack of an eye candy so I'll continue using it with Unity 2D. To me this issue is solved. Closing the thread.

---

