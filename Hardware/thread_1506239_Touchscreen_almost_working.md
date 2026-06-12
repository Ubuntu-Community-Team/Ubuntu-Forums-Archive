---
title: "Touchscreen almost working"
date: 2010-06-10
forum: Hardware
---

### Post by equilar on 2010-06-10
For the last few months I have had Ubuntu 9.1 in my car, controlled by a touchscreen. This worked fine with the eGalax driver.
Last week I upgraded to 10.04 but have since been struggling to get the touchscreen working as it should.

Currently when I touch the screen the cursor jumps to the top left of the screen, I assumed that it was a calibration issue but when I run the callibrator (Touchkit) it says 'No touch controllers found'

Looking at Xorg.0.log it tries to load the eGalax driver but fails saying

                                                ```

(II) LoadModule: "egalax"  
 (II) Loading /usr/lib/xorg/modules/input/egalax_drv.so  
 dlopen: /usr/lib/xorg/modules/input/egalax_drv.so: undefined symbol: xf86GetMotionEvents  
 (EE) Failed to load /usr/lib/xorg/modules/input/egalax_drv.so  
 (II) UnloadModule: "egalax"  
 (EE) Failed to load module "egalax" (loader failed, 7)  
 (EE) No input driver matching `egalax'

```I also tried using the EvTouch Driver but get


                           ```


(**) EVTouch TouchScreen: always reports core events  
 (II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)  
 (**) Option "Device" "/dev/input/mouse1"  
 (EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device  
 Unable to query/initialize EVTouch hardware.  
 [dix] couldn't enable device 10  
 (EE) Couldn't init device "eGalax Inc. Touch"  
 (II) UnloadModule: "evtouch" 

```I have been searching the web and tried all the solutions I could find but no joy so far.
My current xorg.conf is
```

Section "Device"
Identifier "Intel Corporation 945GM"
Driver "intel"
BusID "PCI:0:2:0"
VideoRam 64000
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Intel Corporation 945GM"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
        SubSection "Display"
        Depth 4
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
        SubSection "Display"
        Depth 15
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/touchscreen"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "3900"
    Option "MaxX" "3960"
    Option "MaxY" "195"
    Option "SwapY" "1"
    #Option "SwapXY" "1"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Default Screen"
    InputDevice "touchscreen" "CorePointer"
    InputDevice "dummy"
EndSection

Section "DRI"
    Mode 0666
EndSection 
```

Any help is MUCH appreciated

---

### Post by equilar on 2010-06-11
Using xorg.conf wasnt happy so I installed a fresh copy of 10.04.
Using xinput I was able detect and calibrate my touchscreen
```
xinput set-prop --type=int --format=32 "eGalax Inc. USB  TouchController" "Evdev Axis Calibration" 57 1938 162 1979
```
I have made this into a udev rule but it doesnt run when I plug in the touchscreen or when X starts

---

### Post by equilar on 2010-06-11
WOOHOO!

With help from 'kb1605'
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/549447](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/549447)

"With 10.04 rc, setup.sh from the eGalax driver needs a few  modifications to proper install:
-blacklist file points to /etc/modprobe.d/blacklist, -> change  to /etc/modprobe.d/blacklist.conf
-install script fail if xorg.conf file doesn't exist, -> create file
-install script also fail if ServerLayout section in xorg.conf isn't  present, -> add section"
 Maximka's way of fixing the problem is right.Here is what I have  done, step by step:
sya@7up:~$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer   (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=15	[slave  pointer   (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer   (2)]
&#9116;   &#8627; egalax                                  	id=6	[slave  pointer   (2)]
&#9116;   &#8627; eGalax Inc. Touch                       	id=11	[slave  pointer   (2)]
As you can see "xinput-list" showas two egalaxy devices,
by using the command: <xinput -test "egalax"> and <xinput -test  "eGalax Inc. Touch"> I recognized that the false click to the upper  left corner is done by the device with the name "eGalax Inc. Touch".
 So the next step is to deactivate this device, by taking a look at  the device properties with the command:
 <xinput -list-props "eGalax Inc. Touch">  and afterwards  deactivating the device with the command:
 <xinput -set-prop "eGalax Inc. Touch" "Device Enabled" 0 >.
 Now the mousepointer moves correctly and there are no false clicks to  the upper left corner.
In my case I also had to start the eGalaxyTouch configuation program and  change the "mouse mode" to "click on touch".
Now im just going to swap my Y axis and im good to go!!!!!!!

---

### Post by equilar on 2010-06-13
xorg.conf
```
Section "Device"
Identifier "Intel Corporation 945GM"
Driver "intel"
BusID "PCI:0:2:0"
VideoRam 64000
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Intel Corporation 945GM"
    DefaultDepth 24
    SubSection "Display"
        Depth 1
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
        SubSection "Display"
        Depth 4
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 8
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
        SubSection "Display"
        Depth 15
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 16
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth 24
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "ServerLayout"
        InputDevice "EETI" "SendCoreEvents"
    Identifier "Default Layout"
    Screen "Default Screen"
    InputDevice "dummy"
EndSection

Section "DRI"
    Mode 0666
EndSection
### Touch Configuration Beginning ###
Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
        Option "SkipClick" "1"
    Option    "MinX"        "16"
    Option    "MaxX"        "1025"
    Option    "MinY"        "761"
    Option    "MaxY"        "1"


EndSection
### Touch Configuration End ###
```
udev rule 98-touchscreen.rules

```
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="EVTouch TouchScreen", GOTO="xorg_touchscreen_end"
    ENV{x11_options.minx}="16"
    ENV{x11_options.maxx}="1025"
    ENV{x11_options.miny}="761"
    ENV{x11_options.maxy}="1"
    LABEL="xorg_touchscreen_end"
```udev rule 99-touchscreen.rule

```
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="egalax", GOTO="xorg_touchscreen_end"
    ENV{x11_options.minx}="16"
    ENV{x11_options.maxx}="1025"
    ENV{x11_options.miny}="761"
    ENV{x11_options.maxy}="1"
    LABEL="xorg_touchscreen_end"
```

---

### Post by equilar on 2010-06-15
After a fresh install (with the touch screen connected through-out) I installed 'evtouch' then created the following rule

/usr/lib/X11/xorg,conf.d/11-touchkit.conf

 ```
    Section "InputClass"
    Identifier "Touchkit Touch"
    MatchIsTablet    "on"
    MatchDevicePath "/dev/input/event*"
    Driver     "evtouch"
    Option    "ReportingMode"    "Raw"
    Option    "Emulate3Buttons"
    Option    "Emultate3Timeout"    "50"
    Option    "SendCoreEvents"    "On"
    Option    "TapTimer"        "200"
    Option    "LongTouchTimer"    "400"
    Option    "MinX"            "78"
    Option    "MinY"            "156"
    Option    "MaxX"            "1929"
    Option    "MaxY"            "1944"
        Option  "SwapY"                 "1"
EndSection
```

---

### Post by bkwsh on 2010-06-21
I used equilars settings and got my eGalax almoust working. 
When I touch the screen (click without moving), the mousepointer always jumps to the previously clicked position. Are there some additional options I can set? Anyone came across similar issues?

---

### Post by thctlo on 2011-12-02
Its realy simpel. 
 
1) go here, and get the drivers. 
[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm) 
 
2) backup you config of xorg.conf remove it. 
( make sure its al back to basic, like new install )
 cd /etc/X11   
 X -configure
 
3) unpack downloaded drivers, and run setup.sh. 
 
reboot the server. 
 
4) touch wil work now, but things are not right. ( for me x-y mouse was incorrect ) 
to fix this. 
login in X, In Aplications-Accessories, you find : eGalaxTouch Utiliy 
Start it and go to tab Tool. 
First do a 4 Pts Calibration, then do 25 points linearization. 
 
After this every thing was working correct for me. 
 
hope this helps someone

---

