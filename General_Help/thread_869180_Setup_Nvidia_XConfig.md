---
title: "Setup Nvidia XConfig"
date: 2008-07-24
forum: General Help
---

### Post by knudsenjoe on 2008-07-24
I'm trying to repair my nvidia settings. I am unable to change my screen resolution. I have the nvidia 'latest' driver, as well as the nvidia settings app. My problem is the 'latest' driver doesn't seem to have an xconfig ability, and if I repair that, i lose the 'latest' driver, all the while still unable to change resolution. Please help.

---

### Post by louieb on 2008-07-24
Running Hardy?
**[What's the new sudo dpkg-configure xserver-xorg]("http://ubuntuforums.org/showthread.php?t=867505")  **

Take a look at post #5.  That worked for me on 2 PCs.

---

### Post by knudsenjoe on 2008-07-24
I tried the above, and I guess what I need is the Nvidia X driver? What is that and how do I get it? I can't tell in synaptic which one I need.

---

### Post by bodhi.zazen on 2008-07-24
Which driver are you running exactly ?

Easiest way to configure is to :

```
nvidia-xconfig
```

Or 

```
gksu nvidia-settigns
```

Save your changes and re-start X

You *may* need to sudo apt-get install nvidia-settings

---

### Post by knudsenjoe on 2008-07-24
nvidia-xconfig:
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

gksu nvidia-settings:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the server.

nvidia-xconfig:

Using X configuration file: "/etc/X11/xorg.conf".
ERROR: Unable to write to directory '/etc/X11'.

Now I'm lost as a cow at a square dance.

---

### Post by bodhi.zazen on 2008-07-24
What nvidia driver are you using ?

If you just installed the nvidia driver, reboot

Otherwise, there is nothing wrong with the nvidia-xconfig command.

You need to re-start X now, that means log out and back in or Ctrl-Alt-Backspace

If you need further adjustments use gksu nvidia-settigns

---

### Post by knudsenjoe on 2008-07-24
Driver = NVidia 'latest'

When I try to run the Nvidia settings, I get:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration...

When I try to do that, as root, I get:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by louieb on 2008-07-24
Unfortunately I have 3rd PC with a Nvidia FX5200 card. Its an older P2-400mHz - 384MB  ram. Just a play and test PC. 
Its has me running in circles.
I go into System>Adminstration>Hardware Drivers and enable  the Nvidia Driver. It comes back and tells me I need to restart.
I restart and  get a blank screen. 
I press Ctrl+Alt+F1 to bring up tty1 logon and enter sudo reboot
It reboots and I select recovery mode from the Grub Menu
I select xfix then select resume normal boot.
Gui come up with a 600x800 resolution.

Wait I'm going to try something else ```
gksudo nvidia-xconfig
``` be back in a bit and let you know how it went.

---

### Post by bodhi.zazen on 2008-07-24
> **knudsenjoe said:**
> Driver = NVidia 'latest'

When I try to run the Nvidia settings, I get:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration...

When I try to do that, as root, I get:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

As I said, there is nothing wrong with that. That output is normal and is telling you a new X config file was make and the old one was backed up.

Did you restart X ?

And what is "NVidia latest" ?? I am not familiar with that terminology. What is "nvidia latest", where did you get it from, and how did you install it ?

---

### Post by knudsenjoe on 2008-07-24
I'm using the nvidia 'latest' video card driver. I mention it in case it helps. I am stuck though, can't figure this out.

---

### Post by louieb on 2008-07-24
Just did some playing around and had partial success.  I now can get the resolution I want but I am using the open source "nv" driver. not the restricted (latest)  "nvidia" driver.

What I did. 

[LIST]
[*]Reboot and  select recovery mode.
[*] I select xfix then select resume normal boot.
[*]run ```
gksudo displayconfig-gtk and selected the display I have
```
[*]run ```
gksudo nvidia-xconfig
```
[*]had to edit /etc/X11/xorg.conf
[LIST]
[*]change the the line** driver "nvidia"** to **driver "nv"**
[*]change the line starting with virtual to my displays max  resolution. (1440  900) in my case.
[/LIST]
 
[*]logoff
[/LIST]
I guess some PCs just can't use the latest driver. I have the FX5200 card in two PCs and they share the same monitor through a KVM switch. 

On one PC I'm able to use the latest driver install via the System>Adminstration>Hardware Driver screen. Can enable Desktop effects and all that good stuff. 
On the other (older) PC that seems to have the same symptoms as yours I am limited to using the open source "nv" driver. and no desktop effects. 

At least on both I can set my screen resolution to what I want.

---

### Post by Mark76 on 2008-07-25
I'm having the same problem of going round in circles with nvidia-settings and nvidia-xconfig.

I try to run settings and it tells me that I need to run xconfig. So I run xconfig in a terminal and restart X Then I run settings and it tells me that I nees to run xconfig. So I...

You can see where this is going ;)

---

### Post by bodhi.zazen on 2008-07-28
It helps if you are able to be a little more specific. 

What video card are you using ?

Which nvidia driver ?

There are several nvidia drivers including nvidia-glx (nv) , nvidia-gle-new (also nv) as well as the proprietary nvidia driver (either downloaded from the nvidia web site and manually installed or using Envy). There is also the proprietary nvidia beta drivers.

So when you say the "lastest nvidia driver" which one is that ? nvidia-gle-new, nvidia stale, or nvidia beta ? If you are using one of the propriratry drivers, did you remove the nvidia-glx driver ?

The problem is that these drives often conflict, so you shoud remove all the drivers and use only one. Some cards require very specific solutions or blacklisting the nv driver.

---

### Post by Britt Torrance on 2008-08-04
This definitely works louieb!  

> **louieb said:**
> Just did some playing around and had partial success.  I now can get the resolution I want but I am using the open source "nv" driver. not the restricted (latest)  "nvidia" driver.

What I did. 

[LIST]
[*]Reboot and  select recovery mode.
[*] I select xfix then select resume normal boot.
[*]run ```
gksudo displayconfig-gtk and selected the display I have
```
[*]run ```
gksudo nvidia-xconfig
```
[*]had to edit /etc/X11/xorg.conf
[LIST]
[*]change the the line** driver "nvidia"** to **driver "nv"**
[*]change the line starting with virtual to my displays max  resolution. (1440  900) in my case.
[/LIST]
 
[*]logoff
[/LIST]
I guess some PCs just can't use the latest driver. I have the FX5200 card in two PCs and they share the same monitor through a KVM switch. 

On one PC I'm able to use the latest driver install via the System>Adminstration>Hardware Driver screen. Can enable Desktop effects and all that good stuff. 
On the other (older) PC that seems to have the same symptoms as yours I am limited to using the open source "nv" driver. and no desktop effects. 

At least on both I can set my screen resolution to what I want.

I have been having the same problem for several days now.  In my case, I can still use the propietary nvidia driver (nvidia-glx-new), but I still needed to set the virtual resolution as shown below.  It is odd though that the displayconfig-gtk, when selecting a generic LCD 1680x1050 Monitor, does not write a modeline for that resolution.  But manually choosing 1680x1050 as the virtual resolution does seem to fix this problem.

Video Card: VGA compatible controller: nVidia Corporation GeForce 8600 GTS
Monitor: Chimei CMV 221D (1680x1050@51)

xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "nvidia"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1400x1050@60" "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

```

---

### Post by fuwindows on 2010-07-05
This thread is old, really old lol....but what [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") is saying about the display about xconfig creating a backup being normal is true. All you need to do, as [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") said is to logout and back in and just like that your changes will take effect immediately

---

