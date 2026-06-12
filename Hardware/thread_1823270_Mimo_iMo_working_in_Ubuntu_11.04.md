---
title: "Mimo iMo working in Ubuntu 11.04"
date: 2011-08-11
forum: Hardware
---

### Post by bradcater on 2011-08-11
I've managed to get an iMo working in 11.04 but have not been successful in rotating it. I'll first give the steps to make it work in landscape:

1) sudo apt-get install xserver-xorg-video-displaylink xinit xserver-xorg xserver-xorg-dev xfonts-base libusb-dev xorg-dev git-core build-essential

2) install /etc/options.d/options/mimo_display.conf

options udlfb console=1

3) install /etc/udev/rules.d/60-displaylink.rules

# DisplayLink devices always have the active configuration on configuration #1
SYSFS{idVendor}=="17e9", SYSFS{bConfigurationValue}=="2", RUN+="/usr/bin/dlconfig /sys%p/bConfigurationValue"

4) install /usr/bin/dlconfig

#! /bin/bash
if [ -e /sys$1/device/bConfigurationValue ]; then
  echo 1 > /sys$1/device/bConfigurationValue
fi;

if [ -e /sys$1/bConfigurationValue ]; then
  echo 1 > /sys$1/bConfigurationValue
fi;

5) edit the /etc/default/grub line that starts with

GRUB_CMDLINE_LINUX_DEFAULT

to read

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=normal nomodeset"

6) sudo update-grub

7) edit /etc/gdm/Init/Default to include the following just below the end of gdmwhich();

XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ]; then
 $XRANDR -o 0
fi

8) sudo apt-get install xinput-calibrator

9) sudo xinput_calibrator; # use the resulting values in your xorg.conf

10) install /etc/X11/xorg.conf

Section "Device"
        Identifier	"dl0"
        driver	"displaylink"
        Option  "fbdev"	"/dev/fb0"
EndSection

Section "Monitor"
        Identifier "monitor0"
EndSection

Section "Screen"
        Identifier "screen0"
        Device "dl0"
        Monitor "monitor0"
	DefaultDepth	16
	SubSection "Display"
		Depth	16
		Modes	"1024x600"
	EndSubSection
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"eGalax Inc. USB TouchController"
	Option	"Calibration"	"239 3887 3849 295"
EndSection

Section "ServerLayout"
        Identifier     "multihead"
        Screen      0  "screen0" 0 0
	InputDevice	"Keyboard0"	"CoreKeyboard"
	InputDevice	"Mouse0"	"CorePointer"
        Option "Xinerama" "Off"
        Option "Clone" "off"
EndSection

Finally, it seems that rotation is not supported. This is a deal-breaker for me. Have I done something wrong that would disallow rotation? System -> Preferences -> Monitors informs me that rotation is not supported.

Thanks

---

