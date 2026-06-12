---
title: "tablet for ubuntu"
date: 2009-05-26
forum: Hardware
---

### Post by qhimq on 2009-05-26
Hi,

I have a hp tx1000 with a clean install of 9.04.

It installed great except for one thing.  The touch screen works somewhat.

When I press the pen against the screen to draw all it does is make the cursor follow the pen, but it doesn't draw.  It only activates the click when I leave the initial spot I started touching.  If I drag from that spot all the cursor does is follow when I should be continuously clicking.

Am I making sense?

here is my xorg.conf
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection


Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/mouse1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection


Section "ServerLayout"
    Identifier "Main Layout"
    Screen 0 "Default Screen" Absolute 0 0
    InputDevice "touchscreen" "CorePointer"
EndSection

```

When I delete all of the touchscreen config in this file, the touchscreen still works the same and nothing changes.  So I'm pretty sure this config file is don't nothing.

Thanks for any ideas.  I really want to use ubuntu for my tablet.

---

### Post by Favux on 2009-05-26
Hi qhimq,

In Jaunty the HAL/.fdi method is used.  The xorg.conf is deprecated.  Have you installed evtouch yet?

There are some threads around dealing with some problems with the touch screen.  This one is new:  [http://ubuntuforums.org/showthread.php?t=1166052&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=1166052&highlight=tx1000)

The launchpad report it links to is here:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)  There are some patches for evtouch to get the touchscreen working better.  And towards the bottom a deb by Ramaddan.

And some larger older threads like:  [http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=1040872&highlight=tx1000)

Good luck!

---

### Post by qhimq on 2009-05-26
THANKS!

```

cd /tmp
sudo apt-get build-dep xserver-xorg-input-evtouch
apt-get source xserver-xorg-input-evtouch
cd xf86-input-evtouch-0.8.7/
rm debian/patches/02-buttonless-device.patch
wget -O debian/patches/02-buttonless-device.patch http://launchpadlibrarian.net/26529094/02-buttonless-device.patch
echo 02-buttonless-device.patch >> debian/patches/series
dpkg-buildpackage
sudo dpkg -i ../xserver-xorg-input-evtouch_0.8.8-0ubuntu3_i386.deb

```

worked for me from Morgan Tørvolt at [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

---

### Post by Favux on 2009-05-26
Hi qhimq,

You're welcome.  Glad you're set up.  Nice of you to share your solution and spread it around.

---

