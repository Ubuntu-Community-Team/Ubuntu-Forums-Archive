---
title: "TrackPad middle mouse scroll on IBM ThinkPad"
date: 2009-08-07
forum: Hardware
---

### Post by Muboo on 2009-08-07
Hello :)

I'm trying to make my middle mouse button on my IBM ThinkPad a scroll-button (as it was on Windows XP). (I can't live without it, to be honest).

After reading around, everybody fixed the issue by adding
```
Option 		"EmulateWheel" "true"
Option 		"EmulateWheelButton" "2"
```
to my "/etc/X11/xorg.conf" under the "InputDevice" section with the "Configured Mouse" identifier. However, I do not have this section. Here is my full xorg.conf file (minus the top comments):

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Any suggestion on how I could emulate the third-mouse scrolling button? Thanks!

-Lazlo

---

### Post by tgalati4 on 2009-08-07
I use the blue center button to open new firefox tabs.  I use two-finger scrolling instead of the trackpoint to scroll.

Try:
cat /var/log/Xorg.0.log | grep TrackPoint

I get:

tgalati4@tpad-Gloria7 /var/log $ cat /var/log/Xorg.0.log | grep TrackPoint
(II) config/hal: Adding input device TPPS/2 IBM TrackPoint
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event9"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
(**) TPPS/2 IBM TrackPoint: (accel) filter chain progression: 2.00
(**) TPPS/2 IBM TrackPoint: (accel) filter stage 0: 20.00 ms
(**) TPPS/2 IBM TrackPoint: (accel) set acceleration profile 0
(II) TPPS/2 IBM TrackPoint: Device reopened after 1 attempts.
(II) TPPS/2 IBM TrackPoint: Device reopened after 1 attempts.

So you could modify xorg.conf (making a backup first):

Section "Device"
     Identifier         "TPPS/2 IBM TrackPoint"
     Option 		"EmulateWheel" "true"
     Option 		"EmulateWheelButton" "2"
EndSection

You could substitute "TPPS/2 IBM TrackPoint" with "Configured Mouse".  Since my T43p has both a TrackPoint and a TrackPad, I don't know which is considered the configured mouse.

Keep your Live CD handy or boot into recovery mode if your display gets messed up due to an xorg.conf error.  This may mess up other settings for the TrackPoint, as there are several as you can see in /var/log/Xorg.0.conf

Also:
apt-cache search trackpad

comes up with mouseemu which performs some type of mousewheel emulation.

Proceed with caution, keep notes, and post what works.

---

### Post by Muboo on 2009-08-07
Hello, thanks for the answer.
Using cat /var/log/Xorg.0.log | grep TrackPoint gives the same result as you.

Adding this code does not work, even after reboot.
```

Section "Device"
Identifier "TPPS/2 IBM TrackPoint"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"
EndSection
```

What is mouseemu? I cannot seem to get it as a package from sudo apt-get mouseemu. Thank you!

---

### Post by tgalati4 on 2009-08-07
Try:

```

Section "Device"
Identifier "Configured Mouse"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"
EndSection

```

apt-cache search trackpad

This shows a program mouseemu under 9.04 (Jaunty Jackelope).

sudo apt-get install mouseemu

It may do the same thing as above, I don't know I haven't used it.

Did a larger google search reveal anything?  Because of all of the TrackPoint switches in Xorg.0.log, I presume there is a way to enable it with a magic Option.

---

### Post by Muboo on 2009-08-08
Hi

I used this instead:
```
Section "Device"
Identifier "Configured Mouse"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"
EndSection
```

And still no result (after restarting X11 and rebooting).
I installed mouseemu, but I do not know how to configure or use it. :confused::(

Thanks for your answers.

---

### Post by tgalati4 on 2009-08-08
man mouseemu
mouseemu --help

It looks like it was programmed for mac's to get around the limitations of a one-button trackpad.

The blue center button scrolling would be nice, but I use two-finger scrolling which works well.

---

### Post by ted209 on 2009-08-11
I just tried this on my thinkpad T22:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

it works perfectly!

---

### Post by tgalati4 on 2009-08-11
Works on a T43p as well.  Thanks for the link.

You don't get the scroll indicator as in Windows, but it works nevertheless.

Thanks again.

---

### Post by jasonhoekstra on 2009-10-18
> [http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

+1, works for me to in Ubuntu 9.10 (Karmic Koala) beta.

---

### Post by ostenfeldt on 2010-03-21
> **ted209 said:**
> I just tried this on my thinkpad T22:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

it works perfectly!
Worked just fine for me to.... Thanks!

---

