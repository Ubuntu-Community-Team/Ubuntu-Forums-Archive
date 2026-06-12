---
title: "Persistent changes to xorg.conf"
date: 2008-10-15
forum: General Help
---

### Post by mvdw on 2008-10-15
Due to a faulty DPMS implementation in my hardware, hardy doesn't correctly recognise the LCD I have attached. I need to change the display properties to 800x600, which is easy enough, but the changes are not persistent between reboots.

How do I get ubuntu to stop overwriting my custom xorg.conf every reboot? I'm open to all ideas, but would prefer not to have to overwrite the generated xorg.conf file and then restart gdm using rc.local or similar.

---

### Post by Spaceman9 on 2008-10-15
What are you using to change the settings?

I don't know if you've already tried this but it's worth a try. Hold down the Alt and F2 keys. That will bring up the run Application window. Type or copy and paste this code into that window and hit Enter

gksu displayconfig-gtk

A window will open. Type in your user password and hit Enter. The Screen and Graphics Preferences window will open. you should be able to find your video card and monitor there and set up everything.

You can use this command to find out what kind of graphics chip you have. Just run this in a terminal

sudo lshw -C display

---

### Post by jerome1232 on 2008-10-15
When you save the xorg.conf file it shouldn't be getting overwritten, if I make one that say 'joebob' I will get one broken X server if I reboot or restart X.

---

### Post by spinifex on 2008-10-16
> **mvdw said:**
> Due to a faulty DPMS implementation in my hardware, hardy doesn't correctly recognise the LCD I have attached. I need to change the display properties to 800x600, which is easy enough, but the changes are not persistent between reboots.

How do I get ubuntu to stop overwriting my custom xorg.conf every reboot? I'm open to all ideas, but would prefer not to have to overwrite the generated xorg.conf file and then restart gdm using rc.local or similar.



Man, lots of Xorg issues today. 

have you tried this entry in your device section.

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
Option "AddARGBGLXVisuals" "True"
Option "OpenGLOverlay" "off"
Option "VideoOverlay" "on"
Option "logo" "1"
Option "Coolbits" "1"
Option "UseEdidDpi" "false"
Option "DPI" "96 x 96"
EndSection

I am actualy running Fedora 9 (neither her nor there really as most xorg's should be the same) through a 40 inch Samsung 1920 x 1080  (650 model) and my resolution is persistent through reboots. 

try this link for my full mess of a xorg (but it works) 

[http://ubuntuforums.org/showthread.php?p=5973331#post5973331](http://ubuntuforums.org/showthread.php?p=5973331#post5973331)

---

