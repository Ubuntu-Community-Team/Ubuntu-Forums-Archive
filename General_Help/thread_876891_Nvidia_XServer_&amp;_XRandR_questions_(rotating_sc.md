---
title: "Nvidia XServer &amp; XRandR questions (rotating screen and maximizing appliactions)"
date: 2008-08-01
forum: General Help
---

### Post by LZZephyr on 2008-08-01
First of all, I have a laptop with an Nvidia Geforce 8400M GS graphics card, on which I have Ubuntu 8.04 installed. I am running both Compiz and Emerald, and have a second monitor hooked up to my laptop which I configure using the Nvidia XServer Settings. The external monitor is up up to be an extension of my desktop (Twinview).
I tried to accomplish the following two things, but could not, and was wondering if someone could tell me whether or not they could be done and how:

1. When I view a video in fullscreen the video will automatically be displayed on my laptop monitor, rather than on the nexternal monitor, however I can maximize applications on the external monitor. Is it possible to choose which monitor to display the video on when it is in fullscreen mode?

2. I recently got the XRandR rotation working, however it will only allow me to rotate the whole desktop (i.e. both monitors at the same time). Is there any way for me to rotate the monitor individually when I have the Nvidia XServer settings as Twinview?

Any help will be appreciated, Thanks.

---

### Post by LZZephyr on 2008-08-02
bump

---

### Post by The Big Chow Mein on 2009-02-21
I would be very interested if anyone has any ideas on this. I would like to rotate a single monitor in a dual screen set up with xserver.

Any help would be great!

---

### Post by LZZephyr on 2009-02-21
Hey Chow Mein, after browsing various other forums I stumbled upon a solution to rotating one monitor:

First of all I'm going to assume you were able to install all your drivers, etc. without any problems. If you don't have them installed, use Envy, or browse the forums if you are having problems (I won't be able to help)

I'm not sure if this works or not with an ATI graphics card, as I have only tried it on my computer with an Nvidia card, but here is how I set up my computer:

First of all, open the nvidia x-server settings with root permission (sudo nvidia-settings) and go to "X Server Display Configuration". In order to be able to rotate each monitor individually, you will have to set the configuration to "separate x screen". If you want to be able to drag windows between both monitors, then also enable Xinerama (unfortunately you can't use compiz with Xinerama enabled).

After you have done this, save the new configuration; now it's time to manually edit the config file.

Open the xorg.conf file whatever editor you prefer (sudo gedit /etc/X11/xorg.conf)

You should see two sections labaled "Monitor"; choose whichever monitor you wish to rotate (it should heopfully give you a model name or something, otherwise you just have to guess). Then add the following lines at the end of the section:

Option "RandRotate" "on"
Option "Rotate" "CCW"

You can either rotate the monitor clockwise or counterclockwise, just enter CW, or CCW in the second line.

After you finish this, save you xorg.conf and restart the xserver, and one of the monitors should be in portrait mode.

If you want to be able to switch back and forth between having both monitors in landscape and one in landscape, and one in portrait, then you can write a little script that swaps the xorg.conf files - just let me know if you are interested in doing so, and I'll show you how I set mine up.

Good Luck

---

### Post by The Big Chow Mein on 2009-02-22
> **LZZephyr said:**
> Hey Chow Mein, after browsing various other forums I stumbled upon a solution to rotating one monitor:

First of all I'm going to assume you were able to install all your drivers, etc. without any problems. If you don't have them installed, use Envy, or browse the forums if you are having problems (I won't be able to help)

I'm not sure if this works or not with an ATI graphics card, as I have only tried it on my computer with an Nvidia card, but here is how I set up my computer:

First of all, open the nvidia x-server settings with root permission (sudo nvidia-settings) and go to "X Server Display Configuration". In order to be able to rotate each monitor individually, you will have to set the configuration to "separate x screen". If you want to be able to drag windows between both monitors, then also enable Xinerama (unfortunately you can't use compiz with Xinerama enabled).

After you have done this, save the new configuration; now it's time to manually edit the config file.

Open the xorg.conf file whatever editor you prefer (sudo gedit /etc/X11/xorg.conf)

You should see two sections labaled "Monitor"; choose whichever monitor you wish to rotate (it should heopfully give you a model name or something, otherwise you just have to guess). Then add the following lines at the end of the section:

Option "RandRotate" "on"
Option "Rotate" "CCW"

You can either rotate the monitor clockwise or counterclockwise, just enter CW, or CCW in the second line.

After you finish this, save you xorg.conf and restart the xserver, and one of the monitors should be in portrait mode.

If you want to be able to switch back and forth between having both monitors in landscape and one in landscape, and one in portrait, then you can write a little script that swaps the xorg.conf files - just let me know if you are interested in doing so, and I'll show you how I set mine up.

Good Luck

Good stuff! Thanks for that.

---

### Post by mir123 on 2009-11-21
Hey LZZephyr, thanks for that HOWTO!  I've been looking for a long while for a way to rotate just one screen on my dual head setup, but I was stuck in trying to do it with TwinView.  I am now browing the web on my rotated screen with my ancient Quadro NVS 280 PCI-E.  Cheers!

---

### Post by Nick Payne on 2009-11-29
You can rotate one screen with Twinview. See [http://ubuntuforums.org/showthread.php?t=1335433]("http://ubuntuforums.org/showthread.php?t=1335433"), where I posted the xorg.conf that does this for me. I prefer Twinview to separate X screens as you can drag windows between screens, and there are no problems with Firefox refusing to open because it is already open on another screen.

---

### Post by skitheo on 2010-06-11
> **Nick Payne said:**
> You can rotate one screen with Twinview. See [http://ubuntuforums.org/showthread.php?t=1335433](http://ubuntuforums.org/showthread.php?t=1335433), where I posted the xorg.conf that does this for me. I prefer Twinview to separate X screens as you can drag windows between screens, and there are no problems with Firefox refusing to open because it is already open on another screen.

Actually, you're using Xinerama, NOT Twinview, so not really a solution. Enabling Xinerama basically is not an option, performance-wise.

---

### Post by tomodachi on 2011-12-01
Well to start with. Yes one can rotate screens with nvidia-settings. But this would rotate BOTH screens. When in twinview mode (in my case it actually just crashes the session and logs you out).


With the "separate X servers config" and xinerama its doable. But oneiric doesn't seem to have ANY proper support for multiple X servers in Unity. Only works in Unity 2d.


in Unity 
The Secondary screen is "flipped" But you cant use the keyboard as input devices on it even if mouse clicking works fine. IT also doesn't allow you to re size or move windows which have been placed on it  And starting applications has to be done from the terminal by setting the "DISPLAY" variable to the second X server.

Far from a usable config. 

Happy hacking!

---

### Post by oldos2er on 2011-12-01
Closed, necromancy.

---

