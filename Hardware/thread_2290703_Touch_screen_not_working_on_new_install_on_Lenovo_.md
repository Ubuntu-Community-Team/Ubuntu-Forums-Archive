---
title: "Touch screen not working on new install on Lenovo yoga 300 11IBY"
date: 2015-08-14
forum: Hardware
---

### Post by SteveTyrer on 2015-08-14
I have just installed ububtu 15.04 64bit as a standalone installation (no windows) Running in UEFI mode on a


Lenovo yoga 30011IBY
Memory 2 Gib 
intel Celeron(R) CPUN2840 @ 2.16GHz x2
Graphics intel BayTrail
64 bit
Disk 28.7 GB


Install went smooth with the only problem during install was the wifi would not work until updates were installed. But I cannot get the touchscreen to work, have searched the forum  and have tried the Touchscreen  guide in the ubuntu wiki, with &#8220;lsusb&#8221; the screen is not listed so I assume its &#8220;serial&#8221; then tried &#8220;screen /dev/ttyS#&#8221; and went from S0 to S20 but I am not sure if this is working correctly as the Terminal reports [screen is terminating] after I enter &#8220;screen/dev/ttyS#&#8221;


Can someone advise please as I have run out of ideas

---

### Post by xt10-20zp9 on 2015-08-15
Same thing here with a Yoga 300 "11IBY" too, but with different specs. (Intel Pentium N3540 with 4gb ram). Everything works except the touchscreen and i don't know anything about touchscreens on Linux, i tried searching a little tho. This Yoga model seems very similar to the "previous" Yoga 2-11" i must say (that i had for a short while before the 300-11). Although with the 2-11" the touchscreen worked on (i think) Manjaro with a 3.18 kernel too (but not Ubuntu 15.04. - And i tried Manjaro too on the 300-11, it doesn't work either.)

---

### Post by andrewandrew on 2015-09-26
I have the same issue.  
First thing I did was install ubuntu 14.04lts when I purchased my Yoga 300 11IBY yesterday.  Would love to get the touch screen working.
And anyone help?

---

### Post by zolartan on 2015-10-24
Also want to buy the Yoga 300 and install Lubuntu on it. Is there already a solution to the touch screen issue and does everything else work as it should?

Would appreciate any info.

PS. Have you tested if the touch screen works with the newly released Ubuntu 15.10?

---

### Post by SteveTyrer on 2015-10-25
Hi Zolartan, have not tried 15.10 so can not say if it fixes the touch screen, but the Yoga 300 has been running on 15.04 for some time now with no problems.
So the only thing not working is the touch screen.

Steve

---

### Post by zolartan on 2015-10-25
Hey Steve, thx for the info. If you find the time it would be cool if you could test the screen by booting from a 15.10 flash drive.

---

### Post by neo_1in on 2015-10-27
> **zolartan said:**
> Hey Steve, thx for the info. If you find the time it would be cool if you could test the screen by booting from a 15.10 flash drive.

I have tested it and touchscreen definitely works on Ubuntu 15.10 as well as ubuntu-gnome 15.10. It works on kubuntu 15.10, though here the screen behaves like a touchpad with fingers acting like mouse pointer.
Didn't use gnome and kde versions as tablet, though unity version DID NOT disable physical keyboard in tablet mode, while gnome version DID present an onscreen keyboard automatically while focusing an input field.

One thing that does bother me is the performance in specific tasks. Both unity and gnome versions froze on me especially while thunderbird/evolution populating exchange emails and wifi behaved quite iffy with gnome (sometimes) and kde (often) versions. I was quite happy with general performance until I encountered these issues.

OT, Interestingly my bluetooth speaker produced better sound output with ubuntu gnome than ubuntu (unity), other conditions being same.

---

### Post by zolartan on 2015-10-27
@neo_1in

Thank you for your report. Nice to hear that touch works with 15.10. Read about the automatic disabling of the physical keyboard under windows and was already curious if it also works under Ubuntu. Perhaps it is possible to activate it in Ubuntu. After all there has to be some sensor detecting if its in tablet mode.

Probably will buy the yoga 300 and test how it runs Lubuntu 15.10.

---

### Post by zolartan on 2015-10-29
Ok, bought it. You all installed Ubuntu in UEFI mode? Is that necessary or has any advantages over not using UEFI mode? Without it I could use the 32bit version which should have lower memory usage. Could be an advantage considering the notebook only has 2gb of ram...

Update (Nov 1st 2015): Tried the 32 bit Lubuntu 15.10 version with legacy mode. Could run it from the usb drive but once installed there came an error that no bootable disk was detected. Switched to UEFI mode and installed the 64bit Lubuntu 15.10 version and works great. Touchscreen works out of the box. Button on the side of the notebook to rotate screen by 180° does not work. Installed xbindkeys added it to the startup applications and created .xbindkeyscr file in home folder with following content:

[I]"xrandr --output eDP1 --rotate inverted; xinput set-prop 'ATML1000:00 03EB:8C3C' 'Coordinate Transformation Matrix' -1 0 1 0 -1 1 0 0 1"
Control + Next

"xrandr --output eDP1 --rotate normal; xinput set-prop 'ATML1000:00 03EB:8C3C' 'Coordinate Transformation Matrix' 1 0 0 0 1 0 0 0 1"
Control + Prior
[/I]
This rotates the [screen]("http://askubuntu.com/questions/95812/how-can-i-rotate-my-display-in-the-most-easy-way") as well as the [touch input]("https://wiki.ubuntu.com/X/InputCoordinateTransformation"). The original button did somehow not work therefore I used control+next and control+prior as shortcuts.

Installed onboard as touchscreen keyboard. Works fine. The only problem I still have is that onboard's emulation of middle and right click does not work.

---

### Post by rYRweRH on 2015-11-01
+1 solved: with kernel 4.2. and higher the touch screen works fine

By the way, what I had to configure personally was the **microphone**. With ** Skype** it didn't work, as the mic is mono, but Ubuntu thinks it's  stereo. What I had to do, was to switch one of the channels to zero, for example the left mic input. I had to:

1. open alsamixer in terminal. Change with TAB key to record settings. Change with RIGHT to "Capture". Put the mic level on the right side with key "e" to maximum, the left side with key "y" to zero (h for help, ESC to quit alsamixer).

2. in Skype | Settings |  Audio, I had to deaktivate the automatic sound adjustion, as otherwise Skype leveled the mic within some seconds from 100% to 0 %.

3. That's it.

 I got the idea from this link: [http://yubinkim.com/?p=240](http://yubinkim.com/?p=240)

Greetings, spectas

---

