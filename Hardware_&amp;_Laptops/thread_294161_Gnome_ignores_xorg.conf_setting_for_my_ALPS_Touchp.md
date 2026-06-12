---
title: "Gnome ignores xorg.conf setting for my ALPS Touchpad... :("
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by RedStarLabs.org on 2006-11-06
Gnome completely ignores all settings from xorg.conf for my ALPS Touchpad on my Sony Vaio FS415S!
All settings take effects only after restarting X... Why?

Should I restart X **every time** to have my touchpad working?

I tried a lot of solutions from this forum without success...

The only thing I found was this gconf key: /desktop/gnome/peripherals/touchpad
I tried setting "off" to "true" but it doesn't work...

Help please! (and sorry for my bad english :)

---

### Post by larsemil on 2006-11-06
i have had kind of the same problem with my usbmouse. have to disconnect it and reconnect it to use it every second time i start my computer. have not found a solution though.

---

### Post by moosesoom on 2006-11-16
Same problem here:

Toshiba Satellite M70-166 / Ubuntu Edgy
Alps GlidePoint found by Ubuntu 

I need to disable tap click....but....

Synaptics settings: everything's allrite only after an X restart with CTRL-ALT-BACKSPACE

Alps settings: cannot access gnome: at login screen after username and password (both already checked....they're right) it turns back to username 

Bye
Mad

---

### Post by WhiskoKid on 2006-11-26
Anyone figured this out yet?  Same problem here, I am also trying to disable tapping on the touchpad.  Although I can try to play with things using synclient, nothing has an effect until the x-server is restarted.

---

### Post by moosesoom on 2007-05-21
It seems Feisty solved all. Or so it goes on my Toshiba.
Now tap-click works fine when I really tap. Not when I simply touch mousepad surface as it used to do with previous Ubuntu releases.

---

### Post by Shadowtester on 2007-05-21
So what is the secret to getting Ubuntu or Kubuntu to detect and identify an alps glidepoint touchpad and configure it in xorg.conf. I have tried both Ubuntu and Kubuntu 6.10 and 7.04 and so far I have had no luck always gets detected as a generic wheel mouse and trying to add a touchpad section to the xorg.conf has not worked yet to allow gsynaptics or ksynaptics to be able to configure the touchpad I really hate tapping. If anyone has a working solution please pass it on I am starting to think we may need a kernal patch to get the touchpads working correctly. Here is a link to another thread on the Alps touchpad problem [http://ubuntuforums.org/showthread.php?t=417492](http://ubuntuforums.org/showthread.php?t=417492) if you do a search you will also find several other threads with people having problems getting synaptics and alps touchpads to work properly seems that for most people they work from the install but only as a generic mouse so you can not configure the touchpad specific functions/settings.

---

### Post by moosesoom on 2007-05-22
As I said in my previous message Feisty is ok with my touchpad. No change (by me) in configuration files.
Tonite I'll look if there's something new in Feisty's xorg.conf.

Which is your laptop make and model?

---

### Post by ndavenport on 2007-05-22
Hi,

I have just intalled feisty and I'm pretty sure the touchpad was working, and then I started messing around with xorg.conf to get the tablet screen rotation working.

I got tablet rotation working with stylus but now my touchpad doesn't work :redface:

Can someone with a working touchpad in festy post their default xorg.conf?

Much Appreciated :-)

Cheers,
Neil

---

### Post by ndavenport on 2007-05-22
Hi,

After my last post I had a closer look at my xorg.conf and realised somewhere along the line the maxtaptime line got set to 0, effectively disabling tap click. I set this line back to 180.

Everything seems to be working just fine.

The relevant parts of my xorg.conf (I think they are all the relevant parts, I haven't used X in years...) are as follows.

N.B. Do NOT just copy and paste this into your xorg.conf, if the Identifiers are different in your set up it will mess up your X, make sure you look at the options and if you do copy and paste then make sure you update your identifiers.

> Section "ServerLayout"

	#InputDevice "P5Mouse1" "SendCoreEvents"
    Identifier     "Landscape"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Alps Glidepoint" "CorePointer"
    InputDevice    "Mouse0" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

> Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 4 5"
    Option         "Emulate3Buttons" "yes"
EndSection

> Section "InputDevice"
    Identifier     "Alps Glidepoint"
    Driver         "synaptics"
    Option         "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "Emulate3Buttons" "yes"
    Option         "SHMConfig" "on"
    Option         "LeftEdge" "120"
    Option         "RightEdge" "830"
    Option         "TopEdge" "120"
    Option         "BottomEdge" "650"
    Option         "FingerLow" "25"
    Option         "FingerHigh" "30"
    Option      "MaxTapTime"    "180"
    # Swap these next two lines to disable tap-click
    #Option         "MaxTapTime" "0"
    Option         "MaxTapMove" "110"
    Option         "MaxDoubleTapTime" "180"
    Option         "ClickTime" "100"
    Option         "FastTaps" "1"
    Option         "EmulateMidButtonTime" "75"
    Option         "VertScrollDelta" "10"
    Option         "HorizScrollDelta" "20"
    Option         "MinSpeed" "0.2"
    Option         "MaxSpeed" "2.5"
    Option         "AccelFactor" "0.06"
    Option         "EdgeMotionMinZ" "30"
    Option         "EdgeMotionMaxZ" "160"
    Option         "EdgeMotionMinSpeed" "15"
    Option         "EdgeMotionMaxSpeed" "15"
    Option         "EdgeMotionUseAlways" "0"
    Option         "UpDownScrolling" "1"
    Option         "TouchpadOff" "0"
    Option         "GuestMouseOff" "1"
    Option         "LockedDrags" "1"
    Option         "RTCornerButton" "0"
    Option         "RBCornerButton" "0"
    Option         "LTCornerButton" "2"
    Option         "LBCornerButton" "2"
    Option         "TapButton1" "1"
    Option         "TapButton2" "1"
    Option         "TapButton3" "3"
    Option         "CircularScrolling" "0"
    Option         "CircScrollDelta" "0.08"
    Option         "CircScrollTrigger" "0"
    Option         "CircularPad" "0"
    Option         "PalmDetect" "1"
    Option         "PalmMinWidth" "10"
    Option         "PalmMinZ" "200"
    Option         "CoastingSpeed" "0"
EndSection


Hope this helps someone.

p.s. If you have a Toshiba Portege m200 and you would like the stylus and the touchpad working great and automatic rotation of the screen when you rotate to tablet mode pm me , I'll be glad to help.

---

