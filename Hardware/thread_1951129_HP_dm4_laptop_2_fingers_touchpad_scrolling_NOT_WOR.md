---
title: "HP dm4 laptop 2 fingers touchpad scrolling NOT WORKING"
date: 2012-04-02
forum: Hardware
---

### Post by bobthe on 2012-04-02
Hello

I have 11.10 installed on my hp dm4 and for some reason my touchpad scrolling is not working. I've made sure to check vertical scrolling through system settings under mouse and trackpad and still nothing is working. Can someone please help me with this?

---

### Post by Bill Z on 2012-04-02
Are there anything in any of your USB ports at boot up?   I have noticed with 11.10 that if something is in the USB port at boot up, I have problems with my touchpad.  So, I remove all USBs and boot now as a work around.  I did notify the Ubuntu guys since I can reproduce this.  I thought it was only a problem with my brand of laptop.

Just a thought.

---

### Post by vinodkhare on 2012-04-06
Same here. I've been using 11.10 since October last year and haven't been able to fix it. Any help will really be appreciated.

---

### Post by bobthe on 2012-04-13
no i dont have anything connected to the usb port. any help please?

---

### Post by rorschachwalter on 2012-04-14
Try updating xserver-xorg-input-synaptics (but don't use the latest version! ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=665004](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=665004))).

The solution may be to stick with xserver-xorg-input-synaptics 1.5.0, which is available at snapshot.debian.org ([here]("http://snapshot.debian.org/package/xserver-xorg-input-synaptics/1.5.0-2/#xserver-xorg-input-synaptics_1.5.0-2")).

It's more likely a driver issue than a settings issue, so upgrading may fix it.

---

### Post by bobthe on 2012-04-16
I tried installing it, but it didn't install correctly!

this is what i got when i tried to install it: 

```

(Reading database ... 128891 files and directories currently installed.)
Preparing to replace xserver-xorg-input-synaptics 1.5.0-2 (using xserver-xorg-input-synaptics_1.5.0-2_amd64.deb) ...
Unpacking replacement xserver-xorg-input-synaptics ...
dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on xorg-input-abi-13; however:
  Package xorg-input-abi-13 is not installed.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.10.99.901); however:
  Version of xserver-xorg-core on system is 2:1.10.4-1ubuntu4.
dpkg: error processing xserver-xorg-input-synaptics (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 xserver-xorg-input-synaptics


```

any other help??

---

### Post by rorschachwalter on 2012-04-16
It looks like you'll also need to install that other package from snapshot.debian.org ([here]("http://snapshot.debian.org/package/xorg-server/2%3A1.11.1.901-2/#xserver-xorg-core_2:3a:1.11.1.901-2")).

Two things:
First, I can't make any guarantees that this will actually fix your problem.
Second, installing these two packages might require a lot of manual messing around with packages, so I highly recommend that you back everything up before you start playing with this stuff and make sure you have a few hours on your hands. Anything xserver related could cause you some major headaches if it doesn't work out smoothly.

---

### Post by xyzzyman on 2012-04-18
You need to replace your /usr/share/X11/xorg.conf.d/50-synaptics.conf with this:

```

Section "InputClass"
  Identifier "touchpad catchall"
  Driver "synaptics"
  MatchIsTouchpad "on"
    # Enable touchpad
    Option "TouchpadOff"        "0"
    # Allow run-time configuration
    # Option "SHMConfig"           "on"  # deprecated
    # Edge Limits
    Option "LeftEdge" "1752"
    Option "RightEdge" "5192"
    Option "TopEdge" "1620"
    Option "BottomEdge" "4236"
    # Speed
    Option "MinSpeed" "01"
    Option "MaxSpeed" "1.75"
    Option "AccelFactor" "0.0398089"
    # Pressure
    Option "FingerLow" "25"
    Option "FingerHigh" "30"
    Option "FingerPress" "256"
    # Tapping Detection
    Option "MaxTapTime" "180"             # 0 disables tap
    Option "MaxTapMove" "221"
    Option "MaxDoubleTapTime" "180"
    Option "SingleTapTimeout" "180"
    Option "ClickTime" "100"
    Option "FastTaps" "0"
    # Tapping as Buttons (number of fingers)
    Option "TapButton1" "1"
    Option "TapButton2" "2"
    Option "TapButton3" "3"
    # Tap Dragging
    Option "LockedDrags" "0"
    Option "LockedDragTimeout" "5000"
    # Tap Gesture Dragging
    Option "TapAndDragGesture" "1"
    # Corner Tap Buttons
    Option "RTCornerButton" "0"
    Option "RBCornerButton" "0"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    # Scrolling Edges
    Option "VertEdgeScroll" "on"
    Option "VertScrollDelta" "100"
    Option "HorizEdgeScroll" "0"
    Option "HorizScrollDelta" "100"
    # Circular Scrolling
    Option "CircularScrolling" "0"
    Option "CircScrollDelta" "0.1"
    Option "CircScrollTrigger" "0"
    # Two Finger Scrolling
    Option "VertTwoFingerScroll" "on"
    Option "HorizTwoFingerScroll" "on"
    # Corner Coasting
    Option "CornerCoasting" "0"
    Option "CoastingSpeed" "20"
    Option "CoastingFriction" "50"
    # Kernel Event Protocol
    Option "GrabEventDevice" "1"
    # Edge Ignore Boundaries
    Option "AreaLeftEdge" "0"
    Option "AreaRightEdge" "0"
    Option "AreaTopEdge" "0"
    Option "AreaBottomEdge" "0"
    # Trackstick
    Option "TrackstickSpeed" "40"
    # Circular Trackpad
    Option "CircularPad" "0"
    # Multi-function Buttons
    Option "ClickFinger1" "1"
    Option "ClickFinger2" "1"
    Option "ClickFinger3" "1"
    # Edge Movements
    Option "EdgeMotionMinZ" "29"
    Option "EdgeMotionMaxZ" "159"
    Option "EdgeMotionMinSpeed" "1"
    Option "EdgeMotionMaxSpeed" "401"
    Option "EdgeMotionUseAlways" "0"
    # Pressure Motion
    Option "PressureMotionMinZ" "29"
    Option "PressureMotionMaxZ" "159"
    Option "PressureMotionMinFactor" "1"
    Option "PressureMotionMaxFactor" "1"
    # Emulations
    Option "EmulateMidButtonTime" "75"
    Option "EmulateTwoFingerMinZ" "40"
    Option "EmulateTwoFingerMinW" "8"
    # Palm Detection
    Option "PalmDetect" "1"
    Option "PalmMinWidth" "10"
    Option "PalmMinZ" "199"
EndSection
```

Gnome's developers decided to only support 'real' two-finger scrolling when you enable it, so 'emulated' two-finger scrolling just doesn't work. If you use that 50-synaptics.conf file, and turn on two-finger in your settings then you're good. I have to use it on my Acer laptop in Ubuntu, Fedora, Arch, etc... (Some distros the file goes in a different folder though)

---

### Post by vinodkhare on 2012-04-19
This works out of the box on Ubuntu 12.04 beta 2.

---

