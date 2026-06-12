---
title: "Acer T230H Touch Screen on Lucid"
date: 2010-04-25
forum: Hardware
---

### Post by lightnb on 2010-04-25
I'd like to get my touch screen working, but the tutorials I've found so far are confusing, old, and/or contain conflicting information.

So far, I've tried installing "xserver-xorg-input-evtouch", and creating an entry in xorg.conf and rebooting. and the monitor part works fine, but it does nothing when I touch it.

Do I want "evtouch" or "mutouch" or "hidtouch"?

I tried following this how to:
[http://ubuntuforums.org/showthread.php?t=1375047](http://ubuntuforums.org/showthread.php?t=1375047)

but the instructions are unclear at the "Compile the xorg module" step.

---

### Post by Ayuthia on 2010-04-25
Based on the first post in that thread, it looks like you should be using hidtouch.  In the second post, it says if you used the [kernel module]("http://lii-enac.fr/en/projects/shareit/hid-quanta.c") that he built (which is most likely what Lucid is using), you will use evdev or the patched evdev that provides multitouch.

---

### Post by lightnb on 2010-04-26
That's where I was confused...

I tried using "evdev" as the driver, but touch does nothing. Is there a way to see if whatever driver I need is part of the Kernel or not?

The "xserver-xorg-input-evdev" package is installed, but "modprobe evdev" produces "FATAL: Module evdev not found."

And with the file you linked to above, hid-quanta.c, what do I do with that? Is that already a patched version, or does the patch get applied to that first? And then somehow it get compiled into the kernel?

UPDATE: It looks like I do have "evtouch_drv.so" and "evdev_drv.so" in "/usr/lib/xorg/modules/input/". That means I don't have to compile anything? Even if it's the wrong driver, shouldn't my screen at least do SOMETHING when I touch it?



My xorg.conf looks like this:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice "Acer T230H" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"
 Identifier      "Acer T230H"
 Driver          "evdev"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by lightnb on 2010-04-26
Well, sudo cat /dev/usb/hiddev0 produces lots of garbage on the terminal as i move my finger around.... but beyond that, nothing. No matter what I try, touching doesn't move the mouse or cause a click to occur.

---

### Post by Ayuthia on 2010-04-26
> **lightnb said:**
> That's where I was confused...

I tried using "evdev" as the driver, but touch does nothing. Is there a way to see if whatever driver I need is part of the Kernel or not?

The "xserver-xorg-input-evdev" package is installed, but "modprobe evdev" produces "FATAL: Module evdev not found."

And with the file you linked to above, hid-quanta.c, what do I do with that? Is that already a patched version, or does the patch get applied to that first? And then somehow it get compiled into the kernel?

UPDATE: It looks like I do have "evtouch_drv.so" and "evdev_drv.so" in "/usr/lib/xorg/modules/input/". That means I don't have to compile anything? Even if it's the wrong driver, shouldn't my screen at least do SOMETHING when I touch it?


The evdev driver is an X.org module so a modprobe is not needed.  The modprobe command is for the kernel module (the compiled hid-quanta.c code).  The hid-quanta.c source that I linked for you is the patched version.  Since you are getting information from the kernel module already (/dev/usb/hiddev0), we just need to either configure the xorg.conf file correctly or else find the correct X.org driver.

We can first check /var/log/Xorg.0.log to see if it tried to attach your touchscreen and failed.  Another thing that would be helpful is to see the results of the udev rules:
```
udevadm info --export-db > udev.txt
```
Please attach the Xorg.0.log and the udev.txt files and we can see what we might need next.

Also, have you created the udev rule from the guide?  It is supposed to create the /dev/usb/quanta_touch link.  If you did not, that could be part of the problem.

---

### Post by lightnb on 2010-04-26
I did create the udev rule and:

```
sudo cat /dev/usb/quanta_touch
```

produces garbage as I move my finger, so I assume the mapping is working correctly.

I had to compress the udev.txt file to get it under the forum's limit, but both that and the xorg.0.log file are attached.

The "Logitech USB-PS/2 Optical Mouse" is the mouse I'm using, so I'm not sure where "Macintosh mouse button emulation" is coming from. Maybe that's the touch screen?

Thanks again for your help!

---

### Post by Ayuthia on 2010-04-26
I am going to review the udev data, but does /dev/input/quanta_touch also work?

---

### Post by lightnb on 2010-04-26
No, "/dev/input/quanta_touch" doesn't exist.

---

### Post by lightnb on 2010-04-26
Got it working!

I found the answer in this post:

[http://ubuntuforums.org/showpost.php?p=8932808&postcount=36](http://ubuntuforums.org/showpost.php?p=8932808&postcount=36)

I used the instructions and the file he gave, and rebooted, and my touch screen seems to be working now. I'm using "hidtouch" as the driver in xorg.conf.

Thanks so much for your help!

---

### Post by Ayuthia on 2010-04-26
That is great to hear!  Congratulations!

---

### Post by lightnb on 2010-04-28
Is there any way to adjust the screen's behaviour?

Sometime when you touch, it moves the cursor, but doesn't "click" there. you have to touch again to get a click. Other times, touching moves the mouse and clicks in one operation. It's really inconsistent.

---

### Post by quadra on 2010-05-17
It worked fine for me, too (Ubuntu 10.04 and Acer T230H). I try to summarize for people who like it as simple as possible:

1) I followed the section "Udev Rules" in [http://ubuntuforums.org/showpost.php?p=8626356&postcount=1]("http://ubuntuforums.org/showpost.php?p=8626356&postcount=1") (maybe not needed?)
2) I followed the steps in [http://ubuntuforums.org/showpost.php?p=8932808&postcount=36]("http://ubuntuforums.org/showpost.php?p=8932808&postcount=36"), starting at the line "sudo apt-get install.." (actually I used make && sudo checkinstall instead of make /make install -> creates a .deb file that simplifies the process next time)
3) I edited xorg.conf (sudo gedit /etc/X11/xorg.conf, it was empty at the beginning)
4) I rebooted
Before I had tested it with the version in the other thread (8626356), no success.

My xorg.conf is shorter, I just added the two sections below which contain the minimum requirements for the T230H.

```
Section "InputDevice"
# I added this for touchscreen T230H
 Identifier      "Acer T230H"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

Section "ServerLayout"
# I added this for touchscreen T230H
	Identifier "Touchscreen"
	InputDevice "Acer T230H" "SendCoreEvents"
EndSection
```

@lightnb: The inconsistent behaviour was observed here, too. I know no workaround. It's not a big problem for me - the problem was already present in Ubuntu 9.10, even a bit worse it seems. Sometimes the Y coordinate of the clicks remained frozen for some time.

---

### Post by mike4ubuntu on 2010-05-18
no luck with this.  I did the udev rules and now have the following:
```

ll /dev/usb
total 0
 drwxr-xr-x  2 root root     100 2010-05-18 08:12 ./
 drwxr-xr-x 17 root root    3960 2010-05-18 08:12 ../
 crw-rw----  1 root root 180, 96 2010-05-18 08:12 hiddev0
 crw-rw----  1 root root 180, 97 2010-05-18 08:12 hiddev1
 lrwxrwxrwx  1 root root       7 2010-05-18 08:12 quanta_touch -> hiddev0

```

Also, when I cat the quata_touch port, and touch the screen, I see seomthing sreaming out of it, but it's not human readable.

looks like the problem is with the X server.

this is my xorg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
# I added this for touchscreen T230H
 Identifier      "Acer T230H"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
# Option          "Device"                "/dev/usb/hiddev0"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

Section "ServerLayout"
# I added this for touchscreen T230H
        Identifier "Touchscreen"
        InputDevice "Acer T230H" "SendCoreEvents"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer T230H"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1680x1050_60_0 +0+0; CRT: nvidia-auto-select +0+0, DF
P: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by everythingsround on 2010-05-18
Thanks for the roundup quadra.

@mike4ubuntu I also get binary data with cat (^Ca1&#65533;T) of course it doesn't translate to be pasted. 

hidDeviceDump /dev/usb/hiddev0 
gives data but then apparently freezes.

I'm wondering if not only an X issue, but an NVidia issue.
Quadra. are you using an ATI video card?

I think I'm in the same boat as Mike. Still very happy for the people who have gotten it working, and very jealous :)

---

### Post by mike4ubuntu on 2010-05-19
yes, it probably is related to the X server.  Looks like the xorg.conf may not be getting picked up.  I'm using a nvidia Quadro NVS 140M video card in a IBM/Lenovo Thinkpad T61 laptop.  I have the nvidia proprietary drivers installed.  Does this only work with the open drivers?  I used the nvidia display utility to generate the /etc/X11/xorg.conf file.  Then I just added the InputDevice config to the generated file.  Is there anything beyond that to get X to recognize the added config?

---

### Post by lightnb on 2010-05-24
I have touch working and nvidia proprietary drivers. I got touch working first, and then installed the nvidia afterwards. The restricted software installer tool could not install them though- I had to install the driver packages manually, and then reconfigure my xorg.conf.

This is what my xorg looks like with both touch and nvidia drivers:

```

Section "ServerLayout"
    Identifier "Touchscreen"
    Screen      0  "Screen0"
    InputDevice    "Acer T230H" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
 Identifier      "Acer T230H"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

#Section "InputDevice"
#    Identifier "dummy"
#    Driver "void"
#    Option "Device" "/dev/input/mice"
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I do have a strange issue where the cursor will randomly jump to the top left (0,0) when you touch, but for the most part it's working. I'm also using a USB mouse in addition to the touch screen.

---

### Post by -mbs- on 2010-05-29
> **Ayuthia said:**
> That is great to hear!  Congratulations!

Can you help me? I did like him, and i get no result on the touch.

---

### Post by -mbs- on 2010-05-29
**Now it's working, but not probely. When i click a folder on the Desktop the mouse cursor is going at the left side at the screen, and its taking the folder with it, if i double click. Is the a way where I can calibrate the screen or something?**

_This is my xorg.conf_

[I]
Section "ServerLayout"
    Identifier "Touchscreen"
    Screen      0  "Screen0"
    InputDevice    "Acer T230H" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
 Identifier      "Acer T230H"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

#Section "InputDevice"
#    Identifier "dummy"
#    Driver "void"
#    Option "Device" "/dev/input/mice"
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection[/I]

[B]In a folder the cursor is not "taking" the folder, but the cursor is at the left side at the screen.

This i before I touch the screen (look at the cursor) [http://peecee.dk/upload/view/248139](http://peecee.dk/upload/view/248139)
And this i after i double click (look again at the cursor) [http://peecee.dk/upload/view/248138](http://peecee.dk/upload/view/248138)

And also my question is how to put 1920x1080 resolution in this config?

Also what about the zoom function with two fingers? And the scrool function like W7

/mbs[/B]

---

### Post by sporniket on 2010-06-02
Hi,

Hidtouch is only monotouch for now, but I started studying how to do it.

Back to your problem :

In the last version, there are some new parameter to add to cope with multitouch devices (read the README file in the archive)

use the hidDeviceDump utility to determine the correct value for option "PacketCount" and "PacketManagement_SubgroupPacketCount"

The screen resolution for the driver are in the lines and seems correct

```
Option "CornerScreenWidth" "1920" # 1920 for 23"
Option "CornerScreenHeight" "1080" # 1080 for 23"

```


use the hidDeviceDump utility to determine the values for the calibration

```
Option "CornerTopLeftX" "0"
Option "CornerTopLeftY" "0"
Option "CornerTopRightX" "1920" # 1920 for 23"
Option "CornerTopRightY" "0"
Option "CornerBottomLeftX" "0"
Option "CornerBottomLeftY" "1080" # 1080 for 23"
Option "CornerBottomRightX" "1920" # 1920 for 23"
Option "CornerBottomRightY" "1080" # 1080 for 23"

```


I wrote a manual that can be downloaded from the [sourceforge project page]("http://sourceforge.net/projects/hidtouchsuite/")

Regards.

---

### Post by -mbs- on 2010-06-12
> **sporniket said:**
> Hi,

Hidtouch is only monotouch for now, but I started studying how to do it.

Back to your problem :

In the last version, there are some new parameter to add to cope with multitouch devices (read the README file in the archive)

use the hidDeviceDump utility to determine the correct value for option "PacketCount" and "PacketManagement_SubgroupPacketCount"

The screen resolution for the driver are in the lines and seems correct

```
Option "CornerScreenWidth" "1920" # 1920 for 23"
Option "CornerScreenHeight" "1080" # 1080 for 23"

```


use the hidDeviceDump utility to determine the values for the calibration

```
Option "CornerTopLeftX" "0"
Option "CornerTopLeftY" "0"
Option "CornerTopRightX" "1920" # 1920 for 23"
Option "CornerTopRightY" "0"
Option "CornerBottomLeftX" "0"
Option "CornerBottomLeftY" "1080" # 1080 for 23"
Option "CornerBottomRightX" "1920" # 1920 for 23"
Option "CornerBottomRightY" "1080" # 1080 for 23"

```


I wrote a manual that can be downloaded from the [sourceforge project page]("http://sourceforge.net/projects/hidtouchsuite/")

Regards.

I'm sorry. I didnt seem to understand excaly what you meen. Shall i put 

	Option    "PacketManagement_HasSubgroup"	"1"
	Option    "PacketManagement_SubgroupPacketCount"	"6"
	Option    "PacketManagement_Strategy"	"0"

in the xorg.conf ?

---

### Post by sporniket on 2010-06-14
> **-mbs- said:**
> I'm sorry. I didnt seem to understand excaly what you meen. Shall i put 

	Option    "PacketManagement_HasSubgroup"	"1"
	Option    "PacketManagement_SubgroupPacketCount"	"6"
	Option    "PacketManagement_Strategy"	"0"

in the xorg.conf ?

Yes, that's it, but vhe value for "PacketManagement_SubgroupPacketCount" must be determined by examining the output of hidDeviceDump. So far, for some devices it's 5, on other devices it's 6. 
It's not so important now, as long as it is "big enough", but it will have to be the correct value when there will be multitouch support.

---

### Post by -mbs- on 2010-07-03
Okay. Thanks alot. Now my only problem is the full resolution 1920x1080 at every startup. The screen is only showing 1176x something every time i start the computer. That kills me :(

> **sporniket said:**
> Yes, that's it, but vhe value for "PacketManagement_SubgroupPacketCount" must be determined by examining the output of hidDeviceDump. So far, for some devices it's 5, on other devices it's 6. 
It's not so important now, as long as it is "big enough", but it will have to be the correct value when there will be multitouch support.

---

### Post by dannyboy9201 on 2011-01-07
i know i am close, but i am not getting my Acer T230H touchscreen functionality to work with Lucid, 
Kernel 2.6.32-27-generic
Nvidia proprietary driver 195.36.24


i am getting output when i use

sudo cat /dev/usb/quanta_touch

I have tried both the xf86-input-hidtouch-9.04.04 and xf86-input-hidtouch-10.05.23 

HidTouch input drivers.

Any ideas,

Would updating to Ubuntu 10.10 fix the problem and automatically add in touch screen support for The Acer T230H?

Regards,
                Daniel.

---

### Post by sporniket on 2011-01-11
I don't know about your specific hardware, but the last version of hidTouch was written for 10.10 version (i.e. for the version of X.org shipped on 10.10)

Besides, some old kernel version may cause malfunction of the touchscreen (in the case reported to me, the touchscreen could not function without restarting X server first, solved with a kernel update)

Anyway I read that touchscreen has better support, so if you can afford to upgrade or install a 10.10, you're likely to be in a better situation.

---

