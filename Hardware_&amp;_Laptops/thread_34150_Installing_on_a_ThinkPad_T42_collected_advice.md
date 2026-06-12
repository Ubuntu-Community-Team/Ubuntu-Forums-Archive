---
title: "Installing on a ThinkPad T42: collected advice"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by emendelson on 2005-05-13
The following page contains everything I've been able to learn about installing and tweaking Hoary on an IBM ThinkPad T42:

[http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html)

Very little of this is new, but it may be convenient to have it all in one place. Corrections and changes are always welcome.

The one crucial issue that I've left out is wireless configuration. I've got this working, but my setup may be different from other people's, and I hope someone more expert than I am can put together a compendium of advice on this tricky question.

Edward Mendelson

---

### Post by GrumpySmurf on 2005-05-14
I have a Thinkpad T41 with the Atheros wireless chipset as well.  I don't remember if this worked off the installation or if I had to install the madwifi package.  I've installed and reinstalled so many distributions on my laptop lately I can't keep them straight.

I'm pretty sure that Hoary worked out of the box on the T41 even with the wireless.

---

### Post by emendelson on 2005-05-14
Atheros wireless works more or less out of the box with the T42 and Hoary (no need to add any drivers), but until you get it right, it tends to have problems. I've got it working very well now, but I've only connected to a very few access points, and I ended up creating profiles in the networking applet for all of them. This seems to be the only way to keep things going. Any other program other than the built-in networking applet causes the wireless connection to drop every three seconds or so.

Edward Mendelson

---

### Post by benplaut on 2005-05-15
[QUOTE=emendelson]Atheros wireless works more or less out of the box with the T42 and Hoary (no need to add any drivers), but until you get it right, it tends to have problems. I've got it working very well now, but I've only connected to a very few access points, and I ended up creating profiles in the networking applet for all of them. This seems to be the only way to keep things going. Any other program other than the built-in networking applet causes the wireless connection to drop every three seconds or so.

Edward Mendelson[/QUOTE]

oh good, so i'm not alone  O:) 

(oh, hi Edward! this is bplaut from thinkpads.com  \\:D/ )

---

### Post by emendelson on 2005-05-15
OK, I've added everything I know about wireless in Hoary to the page linked in the first post. But it isn't much...

Edward Mendelson

---

### Post by Woocash on 2005-05-16
I've installed Ubuntu on T42 without any problems, almost everything is working...

But is it possible to have sth. like "on screen display" while changing the loundness ? 
**Ok, I found it under the link from first post :)** 

Second thing is that I don't know how to run PCMCIA disks... i've got a 128 MB CF and 1GB microdrive and both are not recognised -- how to make it working ?
**Ok, I found it too. Here: [http://linux.highsphere.net/howtos/microdrive.php](http://linux.highsphere.net/howtos/microdrive.php)**

---

### Post by gotmonkey on 2005-06-05
[QUOTE=emendelson]The following page contains everything I've been able to learn about installing and tweaking Hoary on an IBM ThinkPad T42:

[http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html)

Very little of this is new, but it may be convenient to have it all in one place. Corrections and changes are always welcome.

The one crucial issue that I've left out is wireless configuration. I've got this working, but my setup may be different from other people's, and I hope someone more expert than I am can put together a compendium of advice on this tricky question.

Edward Mendelson[/QUOTE]

Thanks for the link to your setup. I was looking for a way to enable the middle scroll. I did loose the ability to paste with the 3 button emulation, but I prefer scroll capabilites anyway.

I installed the ifplugd package and followed the instructions, but it seems to be even slower now. Any ideas?
INTERFACES="eth0"
HOTPLUG_INTERFACES="eth0"
ARGS="-q -f -u0 -d10 -w -I -b"
SUSPEND_ACTION="stop"


Were you able to get the forward page / back page buttons by the arrow buttons working in ubuntu?

---

### Post by emendelson on 2005-06-05
About the forward/back keys, try here:

[http://infinity.hn.org/~pascal/x30/x30.html#keyboard](http://infinity.hn.org/~pascal/x30/x30.html#keyboard)

and here:

[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-December/014440.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-December/014440.html)

I experimented with the first method, and it works, but I prefer the default setup, with the keys working the same way as the left and right arrow.

Haven't noticed the slowdown with ifplugd. This is the first I heard about the problem with oasting - could you explain in detail?

---

### Post by gotmonkey on 2005-06-06
[QUOTE=emendelson]About the forward/back keys, try here:

[http://infinity.hn.org/~pascal/x30/x30.html#keyboard](http://infinity.hn.org/~pascal/x30/x30.html#keyboard)

and here:

[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-December/014440.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2003-December/014440.html)

I experimented with the first method, and it works, but I prefer the default setup, with the keys working the same way as the left and right arrow.

Haven't noticed the slowdown with ifplugd. This is the first I heard about the problem with oasting - could you explain in detail?[/QUOTE]

Thanks, I will give them a try and see if I can get them to work. 

As for the network startup, it might have something to do with my laptop mod's. My T42 is no longer stock. I swapped my wireless card from the ipw2200 b/g card to an Atheros 5211 a/b/g minipci card. It might be getting hung up on connecting to the wireless network. I might just disable the onboard nic to save power and the fact that I don't use it. I will play with it and see if I can decrease my boot time. 

I am thinking about switching back to the ipw200 b/g card or getting the 2915 Intel a/b/g card. 

I have made some upgrades to my T42, It is more like a T42 Xtreme now.

Changes made
1.6 Ghz 2m Cache to 2.0 Ghz 2m Cache
256 PC2700 to 1 gig PC2700
40gig 5400 to 60 gig 7200  
Intel 802.11 b/g to Atheros 5211 a/b/g
1024x768 screen to 1440x1050 screen (that was a pain to install) ](*,) 
Modem daughter card to Bluetooth daughter card 
DvD Combo drive to DVD-RW drive
Regular Battery to Extended Life Battery
Standard charger to tri-mode charger

---

