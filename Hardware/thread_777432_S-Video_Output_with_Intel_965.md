---
title: "S-Video Output with Intel 965"
date: 2008-05-01
forum: Hardware
---

### Post by [z]ephyr on 2008-05-01
Hi all, 
  I'd like to connect my DLP TV to my laptop for use as a second monitor, but I can't get it to display anything at all.  xrandr output:
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2560 x 1600
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV connected (normal left inverted right x axis y axis)
   1024x768       30.0  
   800x600        30.0  
   848x480        30.0  
   640x480        30.0  

I'm using Hardy and, if it matters, the s-video hasn't worked in either Feisty or Gutsy.  I also tried using the 'Screen Resolution' tool in the Preferences menu.  I have slightly more success with that, in that my laptop thinks that there is indeed another screen (I can move the mouse out onto where the TV should be) but there is still no output to the TV.

I've looked on the forums and googled quite a bit, and I haven't found any answers to this issue.

thanks,
zephyr

---

### Post by Syke on 2008-05-01
Did you try something like "xrandr --output TV --on"?

---

### Post by mindracer on 2008-05-10
Hey I have the exact same problem, did you figure everything out? Ive been trying for two days playing with xorg.conf.. updating the the latest development kernel of ubuntu.. using gksudo displayconfig-gtk.. no go.. it detects the TV but nothing

I even removed the i810 intel driver which doesnt support the 965 chipset

someone help!

---

### Post by mindracer on 2008-05-10
OK i got something finally!

Put your laptop to sleep, put your S-video cable in, and start your laptop.  It gives you a clone of your lcd screen.  I cant get an extended desktop to work.

I've been playing on this for two days now.  I updated the latest kernel of ubuntu available.  Go into synaptic repositories and check pre-release updates, etc.  Then i got a message saying theres 80 updates available (including the latest kernel).

My xorg.conf is default settings ubuntu puts.  I tried playing with it with no luck, but the defaults work with the sleep trick.

I'm content for now, i wish i can get it to do extended desktop.  Finally after two days of googling and checking the forums, by accident i get it to work after i had put it to sleep.. I think im gonna submit a bug to ubuntu and see if I can get expert help.


Oh btw in synaptic i always removed xserver-xorg-intel-i810 or something like that.  i810 isnt for intel 965, but its installed anyways.  You might want to uninstall it too, i saw that suggestion in another thread.

---

### Post by mindracer on 2008-05-11
I submitted a bug report to ubuntu about this, if you have anything to contribute please do, you can use my bug report as a reference.  Here's the link:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/229157](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/229157)

---

