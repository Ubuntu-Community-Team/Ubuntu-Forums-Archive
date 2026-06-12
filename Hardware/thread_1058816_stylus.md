---
title: "stylus"
date: 2009-02-03
forum: Hardware
---

### Post by mantater on 2009-02-03
I have tried to get my stylus to work in Ubuntu without much luck. I found this site: [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700) with the instructions I pasted below but whenever I re-boot it just comes up in low-res mode and the stylus still does not work. I do have a question about the second instruction with regards to the "/etc/rc.local file". When I open it up it is completely commented out, by default. Should I enable those first two lines "!/bin/sh -e" and "rc.local" and do I put "/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig" before or after "exit 0"? any help appreciated.

Toshiba uses serial port 0x338 for a touch input, so first you have to install setserial

sudo apt-get install setserial

and add line:

/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig

at the end of /etc/rc.local

Next install xserver-xorg-input-wacom and wacom-tools

sudo apt get install xserver-xorg-input-wacom wacom-tools

and edit /etc/X11/xorg.conf file and add lines:

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/ttyS0"
        Option "Type" "stylus"
        Option "ForceDevice" "ISDV4"
        Option "Mode" "absolute"
        Option "SendCoreEvents" "true"
        Option "Button2" "3"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/ttyS0"
        Option "Type" "eraser"
        Option "ForceDevice" "ISDV4"
        Option "Mode" "absolute"
        Option "SendCoreEvents" "true"
        Option "Button2" "3"
EndSection

and

        InputDevice "stylus" "SendCoreEvents"
        InputDevice "eraser" "SendCoreEvents"
        InputDevice "cursor" "SendCoreEvents"

in section ServerLayout at the end of the same file

Restart and you should be able to use stylus

---

