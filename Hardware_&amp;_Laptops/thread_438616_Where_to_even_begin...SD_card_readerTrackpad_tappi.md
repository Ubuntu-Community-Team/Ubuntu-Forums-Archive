---
title: "Where to even begin...SD card reader/Trackpad tapping"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by darussian12 on 2007-05-09
as a newbie to Ubunru or even the linux world i posted a different problem in the multimedia section that asked this question on the side but thought i would post this in the appropriate forum...

in XP my SD card reader worked great...i updated to Vista and surprise, surprise my SD card bay did not have a driver for it but i got used to it by hooking up my camera directly to the USB port to import the pics. But now that I have Ubuntu dual booting I am wondering how i go about even getting the right driver for my SD slot because in hardware information under ubuntu it says Texas Instruments is the vendor for my Secure Digital Controller...how would i go about making my SD slot usable. all i have been able to find is... [http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci](http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci) but this makes no sense to someone so foreign to linux like me. 

the other issue is my touchpad...in the original thread in the multimedia section I asked a sidetracking question about disabling tapping using my trackpad and i got this as a suggestion..

> and look for the input devices section, specifically something like this:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "MaxTapTime" "0"
EndSection

The "MaxTapTime" is the option that controlls the tap clicking, when it is followed by a 0 in quotes, the feature is off. If these lines don't appear, add them to the same section where your other input devices are found, then check the "SeverLayout" section:

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

and check to make sure that Synaptics Touchpad is listed.

i added the maxtaptime line and set value to 0 but still can click with my trackpad...it;s not something thats going to make me hate linux but its just annoying being able to tap with my trackpad and would like to fix it. anyone have any suggestion how to disable trackpad tapping.

thanks anyone for your help

---

### Post by obviouslyshane on 2007-05-09
No idea about the SD reader, I have a Richo SD card reader that doesn't work either. As for the touch pad, I added the line like it said, and nothing happened, I could still tap to click... Until I rebooted... Now tap too click is disabled... I still wish my card reader would work >_<

---

### Post by llib1234 on 2007-05-09
First step download this: [http://www.geocities.com/dollzrgr8/tifm_install.tar.gz](http://www.geocities.com/dollzrgr8/tifm_install.tar.gz)
Extract it.

Next, copy&paste this into Terminal: sudo aptitude install build-essential linux-headers-`uname -r`
This will download compiling tools

After it finishes, run the file install.sh (in terminal mode) you extracted in a folder. 

Type in Terminal: sudo gedit /etc/modules
Add to that file (on separate lines):
tifm_sd
tifm_7xx1
tifm_core

Restart or logout and then login.
Insert sd card..

---

### Post by darussian12 on 2007-05-10
thanks llib1234, that fixed my SD issues and the touchpad was fixed after restart...now when i get my video file playback issues fixed in the appropriate thread i can get rid of the Vista partition...yesssss

---

