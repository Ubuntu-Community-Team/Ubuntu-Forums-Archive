---
title: "Problem with installing drivers for ati hd6850"
date: 2012-09-02
forum: Hardware
---

### Post by aviusz on 2012-09-02
Hello, newbie here.
 
First of all, i've never had luck with linux (tried to get it running  (in "everything is pefect" mode) several times in my life, yet im still  stuck with windows...), so dont get suprised if it will be 'tragical  case'.
 
Recently i decided to try once more. I went for xubuntu 12.04. Everything  was pretty good until i realised that im running in 1024x768 mode, tried  to switch that in options but its capped at 1024x768.
 
"it begins" part.
 
So I've decided to set out on my journey for looking for some drivers for my AtiCard
I'll lay down everything in numbered list as representation of steps i have made. Hope it will be easier to read.
 
 
[LIST=1]
[*]Tried  to install it trough "Hardware Drivers" (not sure if i recall corectly  name of that app + im on widows currently so i cant rly look it up, hope  you know what i mean). So it downloaded some things, then installed it  giving no errors whatsoever, told be to reboot, so i rebooted, after  grub, it started to load os in normal way (you know... shiny bar + big  "xubuntu" sign), and after 10-14 sec of loading... BOOM black screen. At  this point i didnt knew anything about tty1 so i just reinstalled OS.
[*]then  i tried install drivers trough terminal (l[isted as "Using the Ubuntu  repositories (alternate command line method)" in this guide]("http://help.ubuntu.com/community/BinaryDriverHowto/ATI")) with same effect. no  errors, reboot, black screen, reinstall OS.
[*]then i  tried to just download drivers from AMD ATI page and execute it trough  terminal (not sure if that was said correctly ;s) using```
sudo sh ./amd-driver-installer-8.982-x86.x86_64.run
```   . Same effect. no errors, reboot, black screen. At this point i read  about tty1 (smart man). i managed to uninstall fglrx and reboot into OS  correctly but still without drivers.
[*]then i tried to install drivers trough --buildpkg method from same guide. (yup, u guessed it) Same effect.
[*]I  though i might be a problem with this specific distro so I tried same  thing on fedora (sudo sh ./amd-driver-installer-8.982-x86.x86_64.run  method), with (ofc) same effect
[/LIST]
  
Just a note: I dont rly care about 3d acceleration... I'll prolly still  keep windows for games and some CAD programs. Ofc it would be great if i  could play my (currently) full time game (league of legends, can be  easily lunched trough wine, so they say), but in fact, all i need is  higher resolution, so maybe installing drivers isnt only way to go  (maybe i can force it somehow to set higher resolution?).
 
I googled that problem and searched trough forums, none of it helped (or  maybe i cant search). You guys are pretty much my last hope on my  jurney with linux. 
PS sorry about my poor english, im not native ("no sh.t sherlock") and im still learning it.

---

### Post by QIII on 2012-09-02
With the ATI drivers, the most commonly missed item is to initialize xorg.conf.

The instructions in your item #2 above give instructions for doing that.

Are you absolutely sure you did the step

```
sudo aticonfig --initial
```?

---

### Post by aviusz on 2012-09-02
> **QIII said:**
> 
Are you absolutely sure you did the step?


Wasn't absolutely sure, so i just rerunned whole process. Now i am. Still not working : (.

However here are some things i forgot to mention:

[LIST=1]
[*]Screen goes black cause it stops reciving any signal from graphic card (which means: a) graphic card for some reason is not sending any signal; b) lcd screen is not capable of reading that signal (aka too high resolution or something))
[*]In tty1, when i type ```
sudo reboot
``` it magicly comes back to GUI type loadscreen for 1-2sec and then reboots.
[/LIST]
Not sure if that change/mean anything.

---

### Post by QIII on 2012-09-02
Can you tell me a little more about your system hardware?

Is Ubuntu fully updated?

---

### Post by aviusz on 2012-09-02
> **QIII said:**
> Can you tell me a little more about your system hardware?

Mobo: Asus P5K-PRO
CPU: Intel Core2Duo E8200 (not OC'ed)
RAM: Geil 2gb 800Mhz CL5
GPU: Gigabye HD6850 (factory OC)
PSU: Corsair HX 520W 
HDD1: 160gb Seagate (W7 + Xubuntu)
HDD2: 640gb Samsung F1 (files)
Everything well cooled.
Hope i didnt miss anything 

> **QIII said:**
> Is Ubuntu fully updated?

Yes it is.

---

