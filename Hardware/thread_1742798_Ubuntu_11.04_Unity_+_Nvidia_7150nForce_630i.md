---
title: "Ubuntu 11.04 Unity + Nvidia 7150/nForce 630i"
date: 2011-04-29
forum: Hardware
---

### Post by stadoom on 2011-04-29
Hello community,

I use Ubuntu for 1 year now. I use it on my work and at home. At home I get trouble with graphic cards drivers. After Upgrading to 11.04 Unity wouldn't start, because i havn't installed correct graphic card drivers. I have tried everything to get them work:
- Install drivers from NVIDIA homepage
- Install via System Administration -> Additional drivers

All manuals and howtos don't work any longer, because xorg-configs couldn't found and/or gdm also doesn't work.

My PC is running Ubuntu 11.04 with Gnome on 1024x786 pixels (on a screen with maximal 1280x1024 pixels :( )...

I hope someone can help me.

---

### Post by anti_gravity99 on 2011-04-29
I am having the same problem. After restarting from the upgrade to 11.04 I logged in and it switched to Ubuntu classic even if I pick Ubuntu at the login screen. 

I tried the Nouveau opensource driver and the both nVidia proprietary drivers in "Additional Drivers". I have a Dell D620 with a nVidia Corporation G72M Quadro NVS 110M / GeForce Go 7300.

Anyone have any other ideas?

---

### Post by Gstrazds on 2011-05-10
Hi there.. I have a HP dv6000 notebook - Nvidia Geforce 7150 video.. 

Drivers worked great in 10.04 and 10.10 however moving to 11.04 I seem to have the generic driver 

The Nvidia x-server says;

NVIDIA Driver Version: 270.41.06 Operating System:Linux-x86_64 says it is there loaded and working???

the additional drivers says it is activated but not currently in use? 

so the generic driver which is not the accelerated driver and has the not accelerated driver behavior..

Flipping between Unity and classic where it is supposed be present with the wiggles  is not.. so this is a bug.. 

also the open windows when brought to the for-front go blank; when another window is brought to the for-front it goes blank the window which was in the for-front returns to normal in the background..?

thanks 

Glenn :(

---

### Post by Gstrazds on 2011-05-14
Hi folks...

check your compix settings - discovered it sets everything in unity - it also makes all the menus disappear it you enable incompatible settings/features.. 

Fixed by putting a compix setting icon on the classic desktop.. then fix in the unity desktop.

the Video driver issue appears for me to related to frame controls and frame borders selections; I was using Ambiance flipped to Dust and sand dust so far the blank windows have not come back..

The appearance of the video driver being slow relates to the default settings of compix!

You have to enable the other features; wiggly windows etc to get wiggly windows - which might be obvious to me now:popcorn:

but not before as it was auto enabled..

the compix thing - you need to piddle with it..

Glenn

---

### Post by ZaHACKieL on 2011-05-19
Hi, I'm having similar problems with Nvidia GeForce GT 555M. I'm using Natty with the classic desktop. When I install the restricted drivers I get the "activated but not currently in use" status in Additional Drivers. I tried uninstalling the nouveau driver first and install nvidia after that but didn't work either. Anyone have this graphic card working correctly?

---

### Post by ZaHACKieL on 2011-05-23
Hey guys take a look at this post, it may help : [http://ubuntuforums.org/showthread.php?t=1753799](http://ubuntuforums.org/showthread.php?t=1753799)

---

### Post by haydentech on 2011-05-27
If you are able to log in, but the Unity and GNOME hang, this may be your problem:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/726496](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/726496)

Unfortunately, there does not appear to be a solution yet, other than using Classic with no effects.  It seems to affect nVidia 7XXX cards.

---

### Post by kamakazi20012 on 2011-07-04
I'm having similar issues with the on-board nForce 2 and GeForce 4 architectures.  Everything appears fine until the desktop completes loading; even when testing Ubuntu from a DVD and not installing it.  I tried to install it as well thinking the required drivers would install and fix the problem but this was not the case.

Computer in question is an eMachine W3052 with AMD Sempron 32-bit CPU, nForce 2 and GeForce 4.  Video is unreadable so I can't see or read anything to try and fix the problem.  Works great on my laptop though, but I would like to have a dedicated desktop and bring new life into an old system.  System came with Windows XP SP1 if that helps tell the age.  I would give actual date but I can no longer read the label.

---

