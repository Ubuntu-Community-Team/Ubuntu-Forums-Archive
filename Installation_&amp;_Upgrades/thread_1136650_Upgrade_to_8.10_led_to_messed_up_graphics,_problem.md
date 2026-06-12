---
title: "Upgrade to 8.10 led to messed up graphics, problem remaining after update to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by nixpix on 2009-04-25
Yesterday I was intending to update 8.04 to 9.04, via 8.10. Installation of 8.10 seemingly went fine until reboot. During the boot, as soon as I had selected the latest kernel in GRUB and pressed enter, I got a bunch of text on the screen, appearing very quickly and seemingly repeating itself, accompanied by what seemed like a timer to the left of it. The little I managed to identify said something like '(non-fatal) Bus=00h, Device=02h, Function=00h', though I'm unsure of whether they were all on the same line. Anyhow, I tried with an earlier kernel, but which insisted on that there was some problem involving nVidia, leaving me with an Ubuntu in low graphics mode. 

After some looking around, I decided to update to 9.04 anyhow, in the hope of that it would magically solve the problem. It did not, and this is where I am now. When trying to start kernel 2.6.28-11, it goes very quickly into the fast-moving text part as described above, and it seems to be counting seconds towards infinity. When trying with 2.6.27-11, I have time to read something like 'Aperture beyond 4GB' and then some other word, before it also starts the text-thing. With 2.6.24-23 it somewhat works. After the loading part in which you see the kubuntu logo on my machine, it says something about KDE not being the standard GUI or something (which is true, I run GNOME as my standard but have KDE installed). After this, it tells me something about nVidia and gives me the options of either running in low graphics mode, manually set the graphics or try to identify the error myself. Trying to install the recommended driver (180) simply does not work. With kernel 2.6.22-14 I get more or less the same thing, but with a different message regarding KDE, and either really high resolution but no effects and bad video quality or really low resolution generally. Installing the drivers does not work here either.

I have been trying to figure out how to fix this to no avail and I would be very grateful for any advice what so ever. Where do I go from here?

EDIT: My kern.log is posted [here]("http://rafb.net/p/Very5Q98.html"), if that might be of any help.

---

### Post by nixpix on 2009-04-25
I took a bit of a closer look at the error messages. When I start using 2.6.24-23 I get the message "EE NVIDIA (0): Failed to initialize the NVIDIA kernel module. Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA devis files have been created properly.". When I looked closer at some logs I found something about the nVidia module (169.12) not matching the driver component (180.44). Could this be causing the problem?

Once again, very much grateful for any help.

---

### Post by nixpix on 2009-04-25
Okay, some new info. I decided to screw this and get a new installation using a USB stick and 9.04. I got the same problem as before, with lots of text repeating itself on the screen. As of now I am starting to worry somewhat that I'll have to do a re-install to be able to install, or that I might have to go back to 8.04. Also, I managed to see that during startup the message "Running DKMS auto installation service for kernel 2.6.24-23-generic nvidia (180.44) [fail]" is displayed.

Any ideas on how to solve this?

---

