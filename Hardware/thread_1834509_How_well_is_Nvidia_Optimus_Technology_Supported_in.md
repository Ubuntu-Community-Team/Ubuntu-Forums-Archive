---
title: "How well is Nvidia Optimus Technology Supported in Ubuntu?"
date: 2011-08-27
forum: Hardware
---

### Post by 1R3N1CU5 on 2011-08-27
Hi, 

Sorry if this is the wrong section for this post...but I'm looking forward to buying a laptop that has Nvidia GT 540m graphics cards with Optimus technology...so I'm wondering whether or not it will run fine in Ubuntu?

I know that Optimus technology isn't officially supported by Nvidia...but rather there are projects like "BumbleBee" that claim to actually make it work and stuff....but does it really work? I just want to hear your experience / opinions about it and I'm interested in knowing whether you've been able to run it successfully.

Also let's say I do manage to run the Nvidia card using Bumblebee...but would it support 3d acceleration and would the performance be more or less the same as in windows? Please let me know in details about it and whether you think going for Nvidia would be a risk free investment.


Thanks :)

---

### Post by madjr on 2011-08-27
the guys at [phoronix]("http://www.phoronix.com") usually have latest info on this.

i hear is coming along, but since its unofficial, it will take some time till is perfected and well integrated.

there are some workarounds and 3d does work, but you will need to learn them.

but if you want something that works out of the box NOW, were you dont have to tweak anything, then i dont recommend optimus at this point.

This is just my opinion so far.

---

### Post by realzippy on 2011-08-27
+1
some optimus machines have a switch in the bios for the graphics.
although you don't get the power saving feature which optimus running in windows provides,you can switch this way between full graphics power
or full battery stamina.

---

### Post by madjr on 2011-08-27
> **realzippy said:**
> +1
some optimus machines have a switch in the bios for the graphics.
although you don't get the power saving feature which optimus running in windows provides,you can switch this way between full graphics power
or full battery stamina.

yea, those that have the bios option are the better ones.

---

### Post by realzippy on 2011-08-27
Question is,*if* you need the nvidia graphics at all due to gaming in W7.
Otherwise the Intel graphics core handles 3D *pretty* good in linux.
Btw,meanwhile recurring discussion here...

---

### Post by tesna on 2011-08-27
I'm also have 540M on my notebook, [Bumblebee]("https://github.com/Bumblebee-Project/Bumblebee") works fine, improvement from nothing at all. As for 3D performance linux vs windows I'm not really sure as I can't really comment on that. But benchmark in linux if using nvidia card clearly faster than the onboard

Onboard:
```

~$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x94
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
24.489490 frames/sec - 27.330271 Mpixels/sec
24.830553 frames/sec - 27.710897 Mpixels/sec
24.801449 frames/sec - 27.678417 Mpixels/sec
24.862092 frames/sec - 27.746094 Mpixels/sec

```

540M:
```

~$ optirun glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCI/SSE2
81.747748 frames/sec - 91.230487 Mpixels/sec
77.183486 frames/sec - 86.136770 Mpixels/sec
80.430669 frames/sec - 89.760626 Mpixels/sec
76.905292 frames/sec - 85.826306 Mpixels/sec

```

EDIT: one more thing, I still can't get the backlight/brightness control to work with keyboard shortcut. The brightness bar is there (increasing/decreasing) but the intensity did not change.

---

### Post by madjr on 2011-08-27
> **tesna said:**
> 

EDIT: one more thing, I still can't get the backlight/brightness control to work with keyboard shortcut. The brightness bar is there (increasing/decreasing) but the intensity did not change.

there is a small workaround/trick for that meanwhile, using the command line (your shortcut keys wont work, but you will still be able to change brightness by typing a number).

it was a long time ago , i will see if i can find it.

**edit:** nvm, i found it (had a bookmark):

*setpci -s 00:02.0 F4.B=XX*

where XX is a number from **11 to 99** (safe numbers imo)

actually is from 00 to FF - the numbers are hexadecimal

**warning**: dont use 00 or your screen will go total black and FF will make it white! You wont be able to see nothing on your screen (and not sure, but i think the config saves even if you reboot). If that happens may need to chroot from a live-cd.

[http://www.linlap.com/wiki/asus+ul80vt](http://www.linlap.com/wiki/asus+ul80vt)

would be cool if someone made a little tool or applet that uses that command and instead of typing a number, let u move a slider or use the mousewheel :p

or 3 shortcuts on the desktop: bright, mid and dim

---

### Post by tesna on 2011-08-27
> **madjr said:**
> there is a small workaround/trick for that meanwhile, using the command line (your shortcut keys wont work, but you will still be able to change brightness by typing a number).

it was a long time ago , i will see if i can find it.

**edit:** nvm, i found it (had a bookmark):

*setpci -s 00:02.0 F4.B=XX*

where XX is a number from **11 to 99** (safe numbers imo)

actually is from 00 to FF - the numbers are hexadecimal

**warning**: dont use 00 or your screen will go total black and FF will make it white! You wont be able to see nothing on your screen (and not sure, but i think the config saves even if you reboot).

[http://www.linlap.com/wiki/asus+ul80vt](http://www.linlap.com/wiki/asus+ul80vt)

would be cool if someone made a little tool or applet that uses that command and instead of typing a number, let u move a slider or use the mousewheel :p

Thank you for your help, but unfortunately it does not work on my laptop:(. I have Acer 4750G (sandy bridge) with Intel + Nvidia 540M (optimus).

---

### Post by 1R3N1CU5 on 2011-08-27
Thanks for sharing your experience & giving me pointers guys...but let's say I decided to play safe & go for ATI Radeon HD 6650m....what I'm wondering is....how well would that work on Linux?

I mean I've owned a Radeon HD 5450 graphics card in the past and there didn't seem to be much problem with that...other than the mouse cursor hanging for a second when I move it at the right hand, bottom corner of the screen (using the latest ATI CCCLE)....but how is the support for 6000's series in Ubuntu?

Does everything work fine out of the box or are the drivers lacking some stuff?

I don't really play that much of games, may be warcraft sometimes....and mainly use linux for coding...so I'm really starting to wonder if I would be needing these high end graphics card if it's not worth running them on Linux.

Thanks!

---

### Post by madjr on 2011-08-27
> **1R3N1CU5 said:**
> Thanks for sharing your experience & giving me pointers guys...but let's say I decided to play safe & go for ATI Radeon HD 6650m....what I'm wondering is....how well would that work on Linux?

I mean I've owned a Radeon HD 5450 graphics card in the past and there didn't seem to be much problem with that...other than the mouse cursor hanging for a second when I move it at the right hand, bottom corner of the screen (using the latest ATI CCCLE)....but how is the support for 6000's series in Ubuntu?

Does everything work fine out of the box or are the drivers lacking some stuff?

I don't really play that much of games, may be warcraft sometimes....and mainly use linux for coding...so I'm really starting to wonder if I would be needing these high end graphics card if it's not worth running them on Linux.

Thanks!

well if you dont game much, maybe is better to stick with 1 card solution.

and even today's intel cards have enough power to run warcraft just fine, plus are good with the battery.

As for the 6xxx they should work with the official driver, but you should search for reviews first and/or check phoronix.

---

### Post by madjr on 2011-08-27
> **tesna said:**
> Thank you for your help, but unfortunately it does not work on my laptop:(. I have Acer 4750G (sandy bridge) with Intel + Nvidia 540M (optimus).

sorry to hear that, but maybe the command works with 1 of the cards, have you tried on both?

or there could be a specific command for your cards, i would research those commands.

---

### Post by tesna on 2011-08-28
> **madjr said:**
> sorry to hear that, but maybe the command works with 1 of the cards, have you tried on both?

or there could be a specific command for your cards, i would research those commands.

Thanks for your help. But I've found a solution, by installing [this]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")  (modified kernel, gnome power manager, etc) I finally able to control the backlight :) 

Btw, for Thread Starter, I'm sorry for hijacking your thread :)

---

### Post by madjr on 2011-08-28
> **tesna said:**
> Thanks for your help. But I've found a solution, by installing [this]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")  (modified kernel, gnome power manager, etc) I finally able to control the backlight :) 

Btw, for Thread Starter, I'm sorry for hijacking your thread :)

cool you found a solution and is great that this fix for the backlight will finally be available in ubuntu starting 11.10 !

---

