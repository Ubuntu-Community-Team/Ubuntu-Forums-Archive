---
title: "nvidia and screen resolution problems..."
date: 2009-07-08
forum: Hardware
---

### Post by nukedathlonman on 2009-07-08
I'm working on getting my laptop working properly (Dell Vostro 1720 with Intel 6570 Core 2 Duo, 4gb RAM, 250G 7200 RPM SATA HD, DVD writer, nVidia GeForce 9600M GS (512M memory), Broadcrum wireless, RT8169 gigabit ethernet, and bluetooth module), and I have need to switch to lower screen resolutions at times to play some of my games.  

The problem I'm having is out of the box is Ubunutu (and Kubuntu) will only see the native resolution of my display - 1920x1200.

I found this page: [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

Using the instructions listed under "Problem: The LCD's maximum resolution is detected automatically, but lower resolutions are not available".  I followed the directions and used [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) to make up the modelines I needed.  Now this first test I was using the open source "nv" Xorg driver.  It worked with out a hitch and I can change my display resolutions from as low as 320x240 on up to the native resolution of the panel with out any problems.

So I then installed the closed source nVidia 180 drivers. From a command terminal I follow the same directions except I changed the display name from LVDS to default (xrandr reported that as the display instead of LVDS).  When I test any of the added resolutions, it the screen flickers for a brief second, & then restores back to the native resolution of the display with xrandr spiting out the message "xrandr: Configure crtc 0 failed".

So it's a semi go - as in it only works with the "nv" driver meaning I must forgo 3D acceleration. :-(  Any idea how I can get this working with the closed nVidia drivers?

---

### Post by shatterblast on 2009-07-09
I think you can alter the Resolution from directly inside the NVIDIA X Server.  That is located under:

System -> Administration -> NVIDIA X Server -> X Server Display Configuration

After that, you should press the button for "Detect Displays."

---

### Post by nukedathlonman on 2009-07-09
> **shatterblast said:**
> I think you can alter the Resolution from directly inside the NVIDIA X Server.  That is located under:

System -> Administration -> NVIDIA X Server -> X Server Display Configuration

After that, you should press the button for "Detect Displays."


I think you just miss understand the issue I'm having.

nVidia's configuration is only giving me ONE resolution - 1920x1200.

Yes, that great for general desktop use, and yes, it looks great because it is the native resolution of my display.  But it's totaly useless when I want to play a game that uses another resolution - Starcraft uses 640x480 resolution for example.

Now StarCraft is one of the few games that works, but only takes up 1/3 of the screen - rather hard to really play the game when it's only showing up on 1/3 of the screen and the screen is already small at 17".

Other games simply terminate because the resolution they resquest is NOT avalible.  I can only get other resolutions if I use the "nv" driver instead of the "nvidia" driver, and only when I manually add the resolutions from a command prompt as I did in the first post.

---

### Post by nukedathlonman on 2009-07-09
bump

---

### Post by nukedathlonman on 2009-07-09
Did more digging and I believe I found the problem - or bug rather.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)

Not solved yet, but thanks! :popcorn:

---

### Post by shatterblast on 2009-07-09
You could take a risk and try the following:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

I have not tested the contents.

---

### Post by nukedathlonman on 2009-07-09
I'll give it a spin, but I don't think that will work.  I've rechecked the non-accelerated "nv" driver, and it still shows Edid fail with dccprobe.  Thats probably why I have to add the lower resolutions manualy with xrandr.  I think for the time being I'll have to continue to use my trusty old desktop to game at home instead of at the coffee shop. :-)

---

### Post by nukedathlonman on 2009-07-11
Confirmed - untill I get readable Edid data, I'm stuck @ 1920x1200 resolution.  I did try to ignore edid data and manualy add in modelines, but the colosed nvidia driver does not like doign that at all.  Hopefully this will get fixed at some point, in the mean time I'll just have to use the nv driver with the modelines manualy added in as described int eh first post (which does not work with the closed nvidia driver's).

---

### Post by shatterblast on 2009-07-13
You could also try a different account for the different monitor.  I think it's possible to keep different configurations for the video for different log-in names.  Also in addition to my previous suggestion, it might also help to try the 190.x drivers by enabling "Pre-Released Updates" in the Updates tab of the Software Sources window.  Apparently, that will cover the OpenGL portion where as the PPA possibly will not.

---

