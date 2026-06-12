---
title: "Wacom Cintiq Companion Hybrid"
date: 2013-10-17
forum: Hardware
---

### Post by osarusan on 2013-10-17
The Wacom Cintiq Companion Hybrid came out this month, and it is an amazing piece of hardware. (For those of you who don't know, it is an android tablet which turns into a Wacom Cintiq 13HD when plugged into a PC via HDMI and USB). It comes with out-of-the-box support for Mac and Windows, but not for linux. While I wouldn't expect anything to be ready so soon after a new piece of hardware is released, I'm curious if anyone knows if anything is being done to make this tablet work with Ubuntu.

---

### Post by Favux on 2013-10-18
Hi osarusan,

You're correct in that support was submitted upstream to the kernel.  Even if they've accepted it the support won't be in a Distro release for a bit.

But support for the Cintiq Companion was included in the latest input-wacom release 0.19.0.  According to Jason with it and a udev rule you should be able to get it working.  See this linuxwacom-discuss thread:  [http://sourceforge.net/p/linuxwacom/mailman/message/31503335/](http://sourceforge.net/p/linuxwacom/mailman/message/31503335/)  Notice the udev rule is included as a download link.

---

### Post by osarusan on 2013-10-18
Thanks Favux!

I found this thread via Google but I wasn't really sure what to do with it. Can you clarify it for me?

If I place the 10-cintiq-companion-hybrid.rules file in /etc/udev/rules.d/ is that enough? Or will I have to manually compile the driver as well?




Edit: I've gotten the hybrid working as a monitor now. It doesn't auto-rotate, so I will have to manually rotate it for now until I figure out how to get to to auto-rotate... can't seem to get the stylus working yet either, but it's a start!


Edit: I got the wacom stylus working! All I did was install the kernel module as per that email thread. It was pretty easy!

---

### Post by Favux on 2013-10-18
> I found this thread via Google but I wasn't really sure what to do with it. Can you clarify it for me?
To get the Companion working when attached to the computer you need a Wacom kernel driver/module (wacom.ko) that supports the Companion.  That's what Jason is saying, input-wacom-0.19.0 has a wacom.ko that works for the Companion.  So you'll need to compile it on the computer you attach the Cintiq to.
Edit:  Nice job!  :)
> If I place the 10-cintiq-companion-hybrid.rules file in /etc/udev/rules.d/ is that enough? 
I gather the udev rule is so the computer is able to transfer files between the Companion's Android system and itself.

---

### Post by osarusan on 2013-10-19
Yeah, the udev rule was so the system recognizes it as a device and lets me transfer files. Getting it to work as a stylish was very easy, just by adding that kernel module and rebooting. The tablet works great now, though I haven't attempted to set the tablet buttons yet, and I ended up disabling the touch screen as it was interfering with GIMP every now and then. This is a great little tablet! I think I will be selling my larger Cintiq display now. :D

Now if only GIMP could run on android.......




By the way, Favux, do you know if XFCE has a graphical calibration tool for a wacom stylus? The one that comes with Ubuntu/Unity is excellent, but when I log in to xfce the tablet defaults to stretching across both of my monitors. I can do the math and set it up with xsetwacom, but it being a visual tool I prefer to set it up graphically, just in case the math and the visual proportions are off...

---

### Post by Favux on 2013-10-19
Is xinput_calibrator available?  Search the Software center for 'Calibrate Touchscreen'.  That might work.  It seems to me the Gnome dev.s just finished working on the Wacom applet's calibration some more.

---

### Post by osarusan on 2013-10-19
Its there, but it has the problem of fitting the entire desktop -- i.e. stretching across both monitors. So it doesn't actually do any good in my situation where I have 2 monitors.
The one in the default Ubuntu desktop puts the calibration screen only on the tablet, so I can calibrate it correctly. xinput_calibrate would work if I only had one monitor, but not with 2...

---

### Post by Favux on 2013-10-19
OK, so xinput_calibrator doesn't run on Android so you end up with the monitor and the Companion.

Can you use Display in System settings to select just the monitor to calibrate?  Does the output of **xrandr** in a terminal help?  Or would that just be for xsetwacom?

---

### Post by osarusan on 2013-10-19
Well, the Android part doesn't matter in this case, because I am using the tablet plugged into the PC. (The Companion Hybrid is an android tablet when unplugged, but when plugged in it turns into a Cintiq 13HD.) xinput_calibrator works as intended, but it doesn't seem to be built for multiple-monitors, so it always stretches the calibration screen across both monitors.

I've been able to use xsetwacom and xrandr to get to a basic usable state in XFCE. Using the MapToOutput option in xsetwacom lets me lock the stylus to the tablet, but the problem is it isn't 100% calibrated. I suppose I could do the same using xsetwacom and manually playing around with coordinates until I find something close to accurate, but that isn't the ideal solution. What would be ideal is using something like xinput_calibrator to calibrate the tablet when it is connected to the PC as a second monitor.

---

### Post by Favux on 2013-10-19
You should be able to get the factory calibration coordinates for the Companion in /var/log/Xorg.0.log.  Get you in the ballpark anyway.

Then I was thinking subtract the monitor off the total coordinates you get with xrandr and xinput_calibrator.  Not what you want I know.  This wiki page probably won't be much use:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)  Besides I have to update it with the Gnome and KDE applet's calibration functions once I get around to playing with them.

---

### Post by osarusan on 2013-10-19
Hmm... I've done that in the past and it works alright, though it's hard to get perfect calibration that way. I guess for now that's as good as it can get for xfce. On the plus side, Ubuntu's/Gnome's Wacom config is now pretty much 100% perfect, even with dual monitors, so I can continue using Gnome for now until it becomes easier to do with xfce. Thanks for the help as always! You are truly an asset to the community!

---

### Post by skidzo on 2014-04-25
Hi, typing in an companion hybrid here having just one wish,
If only i could install ubuntu directly in my companion...

---

