---
title: "[question] how to screen calibrate?"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by fekimoki on 2005-08-01
hi i oftenly switching windows and ubuntu.
well my problem is "screen calibration"
the ubuntu displays a little bit too left, that makes a black empty space on the right side, and an unseen space on the left (sucked in)  ](*,) 

how to counter this? any software to calibrate? :roll:

---

### Post by ph8 on 2005-08-01
[QUOTE=fekimoki]hi i oftenly switching windows and ubuntu.
well my problem is "screen calibration"
the ubuntu displays a little bit too left, that makes a black empty space on the right side, and an unseen space on the left (sucked in)  ](*,) 

how to counter this? any software to calibrate? :roll:[/QUOTE]


If it doesn't do it in windows as well (?) it's a strange one, are all your drivers up to date and/or has Ubuntu guessed the hardware correctly?

---

### Post by fekimoki on 2005-08-01
im sorry i forgot to tell that im to lazy to adjusting the screen button to make it to the right when switching ubuntu / windows. 
my monitor is guessed perfectly by ubuntu btw.

---

### Post by Perfect Storm on 2005-08-01
Do you have your monitor specs?

Example mine, take a good look at the part I haved bolded:
> 
 Model number P992
CRT (19")

Screen dimensions
Preset Image Size
4:3 Diagonal 17.32 inches (440 mm)
Horizontal 13.86 inches (352 mm)
Vertical 10.39 inches (264 mm)
Viewable Image Size (VIS) Diagonal 17.97 inches (456.4 mm)
Horizontal 14.37 inches (365 mm)
Vertical 10.79 inches (274 mm)
Aperture Grille Pitch 0.24 – 0.25 mm
Deflection angle 90°
Phosphor type P22
Faceplate coating AR Coating

Resolution
**Horizontal scan range 30 kHz to 107 kHz (automatic)**
**Vertical scan range 48 Hz to 170 Hz (automatic)**
Optimal preset resolution 1024 x 768 at 85 Hz
Highest preset resolution 1600 x 1200 at 85 Hz
Highest addressable resolution* 1920 x 1200 at 75 Hz
* Addressable means the monitor will sync up to this mode. However, Dell does not guarantee the image will be sized and centered correctly.


So my Xorg.conf files looks like this:

> 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	**HorizSync	30-107**
	**VertRefresh	48-170**


If you got your monitor specs, you just change HorizSync and VertRefresh so they fit your monitor, after that reboot. It solved your screen problems and refresh rate problems. **NB: Be caution! If you make a mistake or an error, it's possible to blow up your monitor**

---

### Post by fekimoki on 2005-08-01
thx for all the good answer. i think there has been a miss understanding..
maybe it caused by my bad english. sory..
what im tryin to say in simple language is: im lazy have to press Menu button on the front panel of my monitor, and press Position H, and then pressing right right right..
this process have to be repeated again when entering windows, only this time i press the left left left... to screen calibrate.

so how to counter this problem? how to adjust the ubuntu's screen position similiar to windows ?

mine is samsung syncmaster 753dfx, crt 17"

.. thx

---

### Post by Xian on 2005-08-01
I'd just do it the easy way...

Set the screen properly in Ubuntu using the monitor hardware settings.
You know....just like you've been doing with the Menu button.

Then the next time you are in Windows go into screen properties.
There you should be able to adjust your screen parameters on the fly.

Now the two should match perfectly.

---

### Post by mapman on 2005-08-13
I've had a similar problem where the screen would all of a sudden shrink or shift to one side, and then I was constantly using the monitor buttons to change the screen settings.  Just recently I updated the horizsync and vertrefresh to my monitor's manual specs and so far things have been great!  I had to update the default ubuntu gave me(in xorg.conf) of horizsyn 28-49 and vertrefresh 45-72 to my specs of horizsync 30-70 and vertrefresh 50-120.  Seems perfect now.....

---

