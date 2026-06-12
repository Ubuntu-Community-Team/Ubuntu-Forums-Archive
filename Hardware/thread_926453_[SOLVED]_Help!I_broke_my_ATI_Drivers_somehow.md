---
title: "[SOLVED] Help!I broke my ATI Drivers somehow"
date: 2008-09-21
forum: Hardware
---

### Post by empeg9000 on 2008-09-21
Hey everyone,
I am a new user. Less than I month. I started with a new Dell Vostro 1000 configured as follows:
AMD Athlon 64 X2 TK-57 (1.9GHz/256KB)
15.4 inch Wide Screen XGA LCD
2GB, DDR2, 533MHZ 2 Dimm
Integrated ATI Radeon X1150 Graphics
I installed 8.04. I installed the xorg-driver-fglrx and enabled the ATI accelerated graphica driver. Everything was going sweet and the laptop has been awesome. However when running Google earth and a few games the screen would flash. The same thing would happen with screen savers. So I was using the Synaptic package manager and I tried a couple other drivers that are listed. Long story short, by mistake I guess I unchecked all drivers and hit update and it uninstalled all my drivers. So I rebooted in the low graphics mode and restarted. I reintalled my ddrivers and put everything back how it was before. However everytime I sstart now it says it cannot detect my graphics settings and says I need to configure my setup. How do I fix this? 
Here is a shot of my /xorg.conf file.

Please help. I don't know where to go from here. Ugh. What a lame first post!

---

### Post by Milkium on 2008-09-22
Dude, Iam in the exact SAME boat.
I hope we get an answer. I just posted a thread about it also.

What's your resolution right now?
It was forcing me into 640x480, but after I installed EnvyNG and followed the instructions, I'm running 800x600. Better, but still not my normal 1280x1024.

I'm getting annoyed.

---

### Post by empeg9000 on 2008-09-22
Yeah I saw yours after I posted mine. What a dope! I am in 800X600 but that's the best I can get. I need to sleep but I am so annoyed I can't seem to sleep. Hopefully someone can help use. I tried using that wiki that someone recommended you to try. It didn't help. When I type fglrxinfo I get the following:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

So I tried following the instuctions to remove the mesa drivers [here]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers"). I got this:
stephen@enzo:~$ sudo apt-get remove xserver-xgl
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114 guile-1.6 libgoffice-0-common libosp5
  libaccess-bridge-java linux-libc-dev libgif4 libhtml-tableextract-perl
  fglrx-kernel-source-envy dkms rhino
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So that didn't work. Ugh.

---

### Post by werries on 2008-09-22
Compiz is not compatible with the restricted source ATI drivers, and thus you see your flickering whenever using anything else graphics intensive.

As for resetting the graphics, my only suggestion is to go to recovery mode at boot up and hit "reconfigure X server".

---

### Post by Milkium on 2008-09-22
We're both getting the same errors...
Damn. I should be getting to sleep also. School tomorrow, and I have to wake up extra early.

I'm just so frustrated...

But chances are that next to no one is going to reply this late at night.

---

### Post by Milkium on 2008-09-22
> **werries said:**
> Compiz is not compatible with the restricted source ATI drivers, and thus you see your flickering whenever using anything else graphics intensive.

As for resetting the graphics, my only suggestion is to go to recovery mode at boot up and hit "reconfigure X server".Wow!
Thank you! This worked. I'm running in 1280x1024.

Except...everything is really small, and my whole screen has been moved to the left, leaving a black space to the right.

I assume this had to do with the resolution, so I went to preferences>screen resolution, and I tried 1024x768. But upon clicking "Apply", everything I have open smears its colors together across the whole screen, making nothing work. So I have to restart.

Any insight on this?

---

### Post by Milkium on 2008-09-22
Nevermind guys.

Everything is solved! In my case at least.
Thanks a lot.

what I did was reset the xserver thing like I was told. But even after that, the resolution settings were still a little messed up. So I ran EnvyNG, and everything was back to normal.

Thanks again.

---

### Post by empeg9000 on 2008-09-22
I tried it last night and it seemed to work and when then I restarted and it went back to how it was before. At that point I gave up and went to bed. I guess I will try again tonight.

---

### Post by werries on 2008-09-22
Try reconfiguring the X server like I said, booting into it normally, and then making sure you have the restricted drivers enabled as usual.
Then, in order to prevent flickering in graphics intensive programs like Google Earth, you need to ensure that the compiz effects are set to none, afterwards you can set em back up if you want.

---

### Post by empeg9000 on 2008-09-22
> Try reconfiguring the X server like I said, booting into it normally, and then making sure you have the restricted drivers enabled as usual.
So after I do that do I let the boot up continue to should I restart at that point and then boot up as normal? I know once I click the restricted driver I will have to reboot again.

---

### Post by werries on 2008-09-23
I would let it boot from there, configure your screen as need be, then restart and see whats going on.

---

### Post by empeg9000 on 2008-09-24
Well I couldn't get it working. Since the install was so knew and I really didn't have anything saved on it yet, I just did a complete reinstall. Kind of a bummer but its working now. Thanks for everyone's replies.

---

