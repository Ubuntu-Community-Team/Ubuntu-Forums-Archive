---
title: "installing a new video card"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by ate50eggs on 2005-06-21
I just got a new Leadtek GeForce 6600. What do I need to do to tell ubuntu that it's there?

---

### Post by intangible on 2005-06-21
Try this:

[list=1]
[*] Make sure the restricted repositories are enabled ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)) then **sudo apt-get update** 
[*] **sudo dpkg-reconfigure xserver-xorg** (To get some sane defaults in your config)
[*] **sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx**
[*] **sudo nvidia-glx-config**
[*] **sudo /etc/init.d/gdm restart**
[/list]

---

### Post by ate50eggs on 2005-06-23
[QUOTE=intangible]Try this:

[list=1]
[*] Make sure the restricted repositories are enabled ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)) then **sudo apt-get update** 
[*] **sudo dpkg-reconfigure xserver-xorg** (To get some sane defaults in your config)
[*] **sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx**
[*] **sudo nvidia-glx-config**
[*] **sudo /etc/init.d/gdm restart**
[/list][/QUOTE]

Thanks for helping. I tried your instructions, but I didn't get it to work. I had to do:
**sudo nvidia-glx-config enable**
instead of just:
**sudo nvidia-glx-config**
to get anything to happen. I'm also not sure that I didn't screw something up going through dpkg-reconfigure. anything to look out for?

If I look at the device manager from the desktop, I see an unknown device in my AGP slot: "unknown (0x00f1)." The bus type for the device says PCI, so maybe I need to specify that somehow?

---

### Post by intangible on 2005-06-23
That should be okay on the device manager.  The device manager in Ubuntu still needs some work to be very useful.  Sorry about the nvidia-glx-config thing, forgot the enable :D.

If you messed anything up with dpkg-reconfigure xerver-xorg, you'd know it, either terrible resolution, or non-working mouse/keyboard in X :D.

To make sure the nvidia drivers are working, type "glxinfo" in a terminal  and look for "nvidia".  You can test out the 3D accel by typing "glxgears" in a terminal and making sure you have a frame-rate over 1000.

---

### Post by Anivair on 2005-07-29
[QUOTE=intangible]Try this:

[list=1]
[*] Make sure the restricted repositories are enabled ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)) then **sudo apt-get update** 
[*] **sudo dpkg-reconfigure xserver-xorg** (To get some sane defaults in your config)
[*] **sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx**
[*] **sudo nvidia-glx-config**
[*] **sudo /etc/init.d/gdm restart**
[/list][/QUOTE]

BAM!  this was it!  I've been trying to get my damned card to work since I got the thing (weeks) and it was the dpkg that finally did it.  You're the man and that is that.

---

