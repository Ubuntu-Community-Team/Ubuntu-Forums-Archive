---
title: "Cannot Disable Trackpad in 10.04"
date: 2010-07-06
forum: Hardware
---

### Post by mdvigi7536 on 2010-07-06
Good morning!

Windows died on me this weekend, and I'm using Linux to get me through until I can order and receive a new computer.  I did volunteer work with Linux two years ago, but I'm still a total rookie.  I'm finding my way around OK, but please speak slowly and use small words.  :-)

So I installed Ubuntu 10.04 on my laptop without much difficulty (yay).  However, I can't seem to turn off the trackpad on my Gateway laptop.  Though you couldn't tell by looking at it, the right mouse button seems to be stuck in the "down" position.  This means that when the trackpad is active, it's impossible to use the mouse.  In Windows, I fixed this by turning off the trackpad using whatever "Synaptics" application was already on there, plugged in a USB mouse, and was all set.

In 10.04, I can't seem to find a way to consistently, permanently disable the trackpad for good.  I have looked online and found several solutions which, if they work at all, work for the session they are used on and then are reset.  

Solutions I have tried that I read online:
1.  Uninstalling "xserver-xorg-input-synaptics" didn't work at all.
2.  Installing "gpointing-device-settings" (which required reinstalling #1).  Worked until restart.  After restart, trackpad was still active, though it seems like the settings for turning the trackpad off were retained.
3.  Installed another control-panel type thing.  I forgot the name--sorry--but I think it might have been called "gsynaptics".  Don't quote me.  Worked until restart as well.  Added a "Trackpad" control to System > Preferences.

I'm hoping one of you will be kind enough to take pity on me and let me know what the secret is. :-)  If I bump the trackpad just once, it takes over and then a restart is required.  For now, I'm using a USB drive with Ubuntu 8.04 on it.  It has an option to disable the trackpad in the mouse control panel that seems to be working just fine.

I'd be so grateful for any advice you could share with me.  Thanks for all your help!

---

### Post by ieee488 on 2010-07-06
see if there is a setting in BIOS

---

### Post by mdvigi7536 on 2010-07-06
I did look in the BIOS and there is nothing there for me to disable, unfortunately.

---

### Post by TVirusotb on 2010-08-06
Same problem that I am having...
I have tried using:
sudo modprobe -r psmouse  
Works until reset but however also disables the trackball, which I am still wanting to use the trackball and completely disable the trackpad.

---

### Post by pania on 2010-08-06
Try using gpointing devices check disable touchpad, then in mouse preferences uncheck all the boxes in touchpad.

---

### Post by cow_racer on 2010-09-12
touchfreeze works for me.

sudo apt-get install touchfreeze

Then run touchfreeze and disable touchpad.

Touchfreeze no longer works on Ubuntu 10.10.  gnome-mouse-property seems to turn on the touchpad even after disable by touchfreeze or by syclient touchpadoff=1

---

### Post by cow_racer on 2010-09-12
You can also turn off the trackpad this way:

gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled false

This works for Ubuntu 10.10 as well.

---

### Post by zawmai on 2010-11-07
> **cow_racer said:**
> You can also turn off the trackpad this way:

gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled false

This works for Ubuntu 10.10 as well.

This is perfect. It works on mine. I'm running a Ubuntu Studio 10.10.
Btw, wht does this code mean. Care to explain? xD

---

### Post by xdunlapx on 2011-01-16
> **cow_racer said:**
> You can also turn off the trackpad this way:

gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled false

This works for Ubuntu 10.10 as well.

I"ve scoured the internet trying to find a way to permanently disable the touchpad. Thank you for sharing this command! It works perfectly. All the other commands/tools I've tried work for 30 seconds and then the touchpad mysteriously reactivates. This fixed it for good. I just added it to my startup scripts and boom. Fixed. Thank you again!

---

