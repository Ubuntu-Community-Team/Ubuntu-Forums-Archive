---
title: "Acer C100 Tablet Functionality Problems"
date: 2008-06-27
forum: Hardware
---

### Post by Kryzn on 2008-06-27
Hello everyone

I am pretty new to Linux so forgive my newbness. To get my Old Travelmate into shape for school I decided to install Xubuntu 6.06 on it ( the 8.04 version, as far as I can tell, did not like my graphics card).

I got most things to run just fine but the tablet functionality is giving me troubles. I followed the guides around the net, both for the C100 and the c110 and I think I am about half way there. 

I managed to get the WACOM tools and the setserial installed, and I have also mapped my Stylus to an internal serial port ( TTYS0). If I force WACDUMP with "-f c100 /etc/ttyS0" the stylus is recognized and registers just fine in the test. However in the graphical environment it refuses to run at all. I have already edited my XORG.CONFG file to reference to the port directly, but that did not get the Tablet working within Xubuntu. I feel the problem must be that the stylus commands are not passed to the graphical interface, but I don't know nearly enough to know what to do now.


I am frankly stuck and would appreciate the help.

Thanks.

---

### Post by Kryzn on 2008-06-29
> **Kryzn said:**
> Hello everyone

I am pretty new to Linux so forgive my newbness. To get my Old Travelmate into shape for school I decided to install Xubuntu 6.06 on it ( the 8.04 version, as far as I can tell, did not like my graphics card).

I got most things to run just fine but the tablet functionality is giving me troubles. I followed the guides around the net, both for the C100 and the c110 and I think I am about half way there. 

I managed to get the WACOM tools and the setserial installed, and I have also mapped my Stylus to an internal serial port ( TTYS0). If I force WACDUMP with "-f c100 /etc/ttyS0" the stylus is recognized and registers just fine in the test. However in the graphical environment it refuses to run at all. I have already edited my XORG.CONFG file to reference to the port directly, but that did not get the Tablet working within Xubuntu. I feel the problem must be that the stylus commands are not passed to the graphical interface, but I don't know nearly enough to know what to do now.


I am frankly stuck and would appreciate the help.

Thanks.

Sorry but bump? I really want to like Linux but without the tablet there is really not much point. 

Thanks again.

---

### Post by Kryzn on 2008-06-29
Sorry for the double post, too. my wireless is also acting up a little

---

### Post by cywhale on 2008-06-30
Got mine (C111) working in Arch Linux, maybe this is what you are looking for:

Put following in /etc/bootmisc.sh:
```
/usr/bin/setserial /dev/ttyS0 port 0x06f8 irq 6 autoconfigure
```

The /etc/X11/xorg.conf (Added the last 3 lines to the ServerLayout section and changed wacom devices):
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Touchpad"  "SendCoreEvents"
	InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice "cursor" "SendCoreEvents"
    InputDevice "stylus" "SendCoreEvents"
    InputDevice "eraser" "SendCoreEvents"
EndSection

Section "InputDevice"
    Identifier "cursor"
    Driver     "wacom"
    Option     "Device"        "/dev/ttyS0"
    Option     "Type"		"cursor"
    Option     "ForceDevice"	"ISDV4"
	Option "Speed" "2.0"
EndSection

Section "InputDevice"
    Identifier "stylus"
    Driver     "wacom"
    Option     "Device"        "/dev/ttyS0"
    Option     "Type"		"stylus"
    Option     "ForceDevice"	"ISDV4"
    Option     "Mode"           "Absolute"
    Option "Speed" "3.0"
EndSection

Section "InputDevice"
    Identifier "eraser"
    Driver     "wacom"
    Option     "Device"        "/dev/ttyS0"
    Option     "Type"		"eraser"
    Option     "ForceDevice"	"ISDV4"
EndSection

```
Then reboot to X.

Using Hardy there was no need for setserial, worked just fine without this line. Just needed to paste the xorg.conf-code.

---

