---
title: "Help with Graphics Display in Ubuntu 7.10."
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by Erky on 2008-04-21
Hey there!
I have a serious problem. A couple days ago, my old monitor broke. So, I went out and bought a new Hanns-G 17" Widescreen  LCD monitor. When I got it home, it hooked up to Ubuntu perfectly, but the resolution was funky. So, I tried to change that. I went to Screens and Graphics and switched the monitor from plug-'n-play to a higher resolution LCD monitor, and I checked the widescreen monitor option. Well, my computer did not like that. When I restarted my computer to allow the settings to take affect, the graphics were all messed up. I can see eveything up until the graphical login menu, which leads me to assume that it is something wrong with Gnome or Xserver. The problem is that the screen appears cut in a bunch of horizontal lines, so that I cannot see a thing. I really need some help, or I will be forced to do a fresh install and lose everything on my computer. Please help! I am attaching a couple of pictures of what happens when I got to anything grpahical. The first picture is the login screen, the second screen is the desktop.

---

### Post by banished_one on 2008-04-21
Dont Panic 

You are seeing those funky lines because refresh rate of the monitor is set wrong at the moment. This is because gnome couldnt recognize your video card(or recognized it wrong) and set some wrong values for your monitor. It can be fixed by configuring your video card without using the gui. I once had a problem like this and solved it using a guide but ill try to find it for you. But your data will be ok just hang on :)

---

### Post by Erky on 2008-04-21
Okay thank you very much. I really hope it works.

---

### Post by banished_one on 2008-04-21
ok i found this i hope it helps im no expert myself :)

[http://ubuntuforums.org/showthread.php?p=2323861](http://ubuntuforums.org/showthread.php?p=2323861)

to sum up the convo in the link

use 
<Ctrl><Left-Alt><F1> to change to a virtual terminal

to back up the settings kinda file use 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

if anything goes wrong use this to replace 
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

use this to change the settings 
sudo dpkg-reconfigure xserver-xorg

---

