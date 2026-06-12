---
title: "messed up display after install"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by Gordonx42 on 2006-01-14
I'm having difficulty getting ubuntu to boot properly. 

live cd works perfectly.

The install goes fine, but when now my machine boots to a display disaster. its difficult to explain, but the screen is just all screwed up. i apologize for not being  able to describe the problem better, but hopefully someone knows what im talking about.

---

### Post by gillentine on 2006-01-15
Yes, I am having the same problem and don't even know how to change any settings considering I can't see my display anymore! Can anyone tell us how to proceed? Is there documentation that I can access for the basic setup problems? Thanks.

---

### Post by Omnios on 2006-01-15
How about giving us some more information. 

 WHat kind of vidio card do you have and what kind of monitor, also posting your xorg-config file may help if you can get to it. 

 A nvidia graphics problem can be as easy as installing nvidia-glx and also I had a similar problem with my P2 and a KTX monitor and all I had to do was lower the monitor settings to get it to work properly. Check your monitor frequency range against what is in your xorg.conf.  One think I tryed was lowering hz range to between 60 to 75 as the xsever tries to drive the monitor at the maximum setting.

---

### Post by christhemonkey on 2006-01-15
try pressing <Ctrl>+<Alt>+<F1> to get into a command prompt.
If you can do that, then you can run
sudo dpkg-reconfigure xserver-xorg
or if your using nvidia graphics card:
sudo apt-get nvidia-glx

---

### Post by dueY on 2006-01-15
Sounds like the same problem I had with my NVIDIA card.  First of all get to the command line and type "sudo dpkg-reconfigure xserver-xorg"  Try using different display drivers.  "vesa" worked very well for me.  "vga" may also work but is very  poor quality.  If you can get into the GNOME gui using either of these then immediately go to your video card's web page and download their proprietary Linux drivers.

---

