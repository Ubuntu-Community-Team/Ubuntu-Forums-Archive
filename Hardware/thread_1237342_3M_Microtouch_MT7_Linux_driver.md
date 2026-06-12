---
title: "3M Microtouch MT7 Linux driver"
date: 2009-08-11
forum: Hardware
---

### Post by grackleman on 2009-08-11
Hi
I'm trying to install a new Micrtouch touchscreen using the MT7  (their Linux driver) driver install. I've tried it in Ubuntu 8.10 and 9.04.  When I ran the install I got warnings 'update etc/init.d/TWDrvSartup – missing LSB header “required-start” and “required-stop”'

The calibrate utuilty worked perfectly (I don't think it uses X) but in the GUI I have no response to touch.

I'm not a programmer and tried adding these but don't know what I need ($syslog, $local_fs, etc).
Here's the section from TWDrvStartup created by the Microtouch MT7 driver. It still didn't work.

### BEGIN INIT INFO 
# Provides: TwDriver 
# Default-Start: 2 5 
# Default-Stop: 0 1 3 4 6 
# Description: Start the MT 7 touch screen driver 
### END INIT INFO

This is what is added to xorg.config

Section "InputDevice"
        Identifier  "MT7TouchScreen"
        Driver      "twxinput"
        Option      "Device" "0"
        Option      "ConvertAtRead" "false"
EndSection

They have a large readme file full of things I don't understand. As far as I can tell, everything is in the correct directory. I'm sure it's something simple for one who knows what  they're doing!! They stress that the driver has to be loaded before X starts. 

Just for fun I put in an old harddrive with Suse 10.0 (boy it's slow compared to Ubuntu), did the install, got no warnings and everything worked. From what I've read, Debian requires those lines in the start script.

Any help would be appreciated

Thanks in advance
Peter

---

### Post by VGM on 2010-02-11
I am facing the same problem.If someone has solved this,can you please help me out.

---

### Post by koalauk on 2010-06-14
Me too having the same issue no luck so far

---

### Post by Ian47 on 2010-08-23
I have this working under ubuntu 10.04 Lucid.

I think the trick was to specify the device for the mouse.

Here's the xorg.conf

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option  "Device" "/dev/input/mouse1"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
EndSection

Section "ServerLayout"
        Identifier "Layout0"
        Screen 0 "Default Screen" 0 0
        InputDevice "Generic Keyboard" "CoreKeyboard"
        InputDevice "Configured Mouse" "CorePointer"
        InputDevice "MT7TouchScreen" "SendCoreEvents"
EndSection


Section "InputDevice"
        Identifier  "MT7TouchScreen"
        Driver      "twxinput"
        Option      "Device" "0"
        Option      "ConvertAtRead" "false"
EndSection

```

The touch screen also works with the evtouch driver.

xorg.conf for evtouch driver

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier "TouchScreen"
        Driver "evtouch"
        Option "Type" "finger"
        Option "Device" "/dev/input/event5"
        Option "ScreenNo" "0"
        Option "MinX" "2600"
        Option "MaxX" "14000"

        Option "MinY" "3000"
        Option "MaxY" "13150"
        Option "SwapX"
        Option "SendCoreEvents" "yes"
        Option "ReportingMode"  "Raw"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option  "Device" "/dev/input/mouse1"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
EndSection

Section "ServerLayout"
        Identifier "Layout0"
        Screen 0 "Default Screen" 0 0
        InputDevice "Generic Keyboard" "CoreKeyboard"
        InputDevice "Configured Mouse" "CorePointer"
        InputDevice "TouchScreen"
EndSection

```

---

