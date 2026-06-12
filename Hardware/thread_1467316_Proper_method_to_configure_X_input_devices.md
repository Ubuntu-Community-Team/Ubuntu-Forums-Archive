---
title: "Proper method to configure X input devices"
date: 2010-04-30
forum: Hardware
---

### Post by John Baptist on 2010-04-30
I have a question about the proper method to configure X input devices. In particular, I'm trying to set up the options for my touchpad, which is controlled by the synaptics driver. (This is on the just-released Ubuntu 10.4, which is great, BTW.)

After playing around with the synclient command, I've discovered that I can use the following command to configure my touchpad to my taste:

synclient TapButton2=3 HorizTwoFingerScroll=1 VertTwoFingerScroll=1 EmulateTwoFingerMinZ=29 EmulateTwoFingerMinW=5 JumpyCursorThreshold=200

My first attempt was to simply take this command, put it in an executable shell script, and add that command to the Startup Applications list. That worked, until I suspended or hibernated, in which case X reverted to its default settings.

My second attempt to was to implement these settings in the X configuration file. I was a little disconcerted to find that xorg.conf no longer exists, but discovered that I could add scripts to /usr/lib/X11/xorg.conf.d/ for a similar effect. Here is the content of the X configuration file that I added to that directory:

Section "InputClass"
   Identifier "touchpad catchall"
   MatchDevicePath "/dev/input/event*"
   MatchIsTouchpad "on"
   Driver      "synaptics"
   # Option "TouchpadOff" "1"
   Option "TapButton2" "3"
   Option "VertTwoFingerScroll"   "true"
   Option "HorizTwoFingerScroll"  "true"
   Option "EmulateTwoFingerMinZ"  "29"
   Option "EmulateTwoFignerMinW"  "5"
   Option "JumpyCursorThreshold"  "200"
EndSection

This file, however, seems to have no effect. I know that the file is being loaded, though, because if I uncomment the line containining "TouchpadOff," then the touchpad is in fact disabled. However, the other settings (e.g., those for allowing two-fingered scrolling) don't take. I suspect that the problem is that my settings are being overwritten somewhere else during X's initialization, but I don't know where. Can anyone help me? Is there some official, approved way of permanently configuring the touchpad in this way, either on a system-wide or user-by-user basis?

The ideal case, of course, would be if gpointing-device-settings allowed setting these particular options; in other ways, it is the best pointing device configurator that I know of.

---

