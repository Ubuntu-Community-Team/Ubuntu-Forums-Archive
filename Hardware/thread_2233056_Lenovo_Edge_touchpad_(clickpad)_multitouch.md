---
title: "Lenovo Edge touchpad (clickpad) multitouch"
date: 2014-07-06
forum: Hardware
---

### Post by hellslinger on 2014-07-06
My Lenovo ThinkPad edge E431 has a Synaptics touchpad on PS/2. I would like to get 3 finger swipes working. The clickpad driver options mostly work: 2 finger scrolling and the multi-finger taps/clicks work perfectly.

I tried mtrack but got a "device could not be configured" error. This is with 'Driver "mtrack"' specified in my xorg.conf.d file I list below.

I also tried touchegg, but it gets no input from the touchpad. I've tried running it as root and in KDE with no effect.

 According to this email: [http://lists.x.org/archives/xorg-devel/2014-March/040963.html](http://lists.x.org/archives/xorg-devel/2014-March/040963.html) the synaptics driver has had the Swipe features enables since 1.7.1. Ubuntu 14.04 has Version 1.7.4. 

I have enabled these features with a new config file in /usr/share/X11/xorg.conf.d/. 

```

Section "InputClass"
	Identifier "clickpad"
	MatchProduct "SynPS/2 Synaptics TouchPad"
	MatchIsTouchpad "on"
	Driver "synaptics"
	Option "ClickPad" "0"
	Option "VertResolution" "100"
	Option "HorizResoltuion" "65"
	Option "HorizHysteresis" "50"
	Option "VertHysteresis" "50"
	Option "TapButton1" "1"
	Option "TabButton2" "3"
	Option "SwipeLeftButton" "10"
	Option "SwipeRightButton" "11"
	Option "SwipeUpButton" "8"
	Option "SwipeDownButton" "9"
	Option "HorizSwipeThreshold" "2"
	Option "VertSwipeThreshold" "2"
	MatchDevicePath "/dev/input/event*"
	
EndSection

```

Is there a way to get 3 finger swipes work? I'm open to using any method, but it seems that mtrack cannot be loaded, and something is wrong with the way events work with this device. I get this error when evdev tries to load:

```

evdev: Mouse0: ioctl EVIOCGBIT for bitmask in EvdevOpenMTDev failed: Inappropriate ioctl for device

```

Any ideas would be appreciated.

---

