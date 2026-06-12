---
title: "Cannot compile Kernel Module for Touch Screen Kit"
date: 2008-11-30
forum: Hardware
---

### Post by quinnteq on 2008-11-30
I am having the worst time trying to install the touch screen kit from lavasoft.  

The guides they provided tell me to build a kernel module from source. Fine.. That sounds easy enough right?  Well, when to "make all" it gives me the following:

```

make -C /lib/modules/2.6.42-21-generic/build SUBDIRS=/home/home/TouchKit/USBSrc modules
make [1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
/home/home/TouchKit/USBSrc/tkusb: struckt usb_device_id is 20 bytes. The last of 6 is:
0x03 0x00 0x23 0x38 0x02 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 
FATAL: /home/home/TouchKit/USBSrc/tkusb: struct usb_device_id is not terminated with a NULL entry!
make [2]: *** [__modpost] Error 1
make [1]: *** [modules] Error 2
make [1]: Leaving directory `/usr/src/linux-headers-2..24-21-generic'
make: *** [build_module] Error 2

```

I googled around and found that the this happens when the code from the device isn't terminated correctly or something, and that somewhere... theres some kind of patch or something?  Does anyone know of this, or know of a work around... or hell, maybe I'm doing something wrong. 

Please, any help would be awesome... this touch screen for a picture frame... and its a gift for Christmas for my mother.

Thanks in advance!

---

### Post by quinnteq on 2008-12-01
*bump*

---

### Post by quinnteq on 2008-12-01
*bump*

---

### Post by quinnteq on 2008-12-02
*bump*

---

### Post by N0YKG on 2008-12-09
The software in question is from eGalax:

[http://home.eeti.com.tw/web20/TouchKitDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/TouchKitDriver/linuxDriver.htm)

The error you are seeing is that the table of USB IDs the module hands to the kernel is not correctly terminated with a NULL entry, so there is no way for the kernel to know how big the table is.

In tkusb.c, change:

 static struct usb_device_id tk_table[] = {
    { USB_DEVICE( 0x1234, 0x0001 )},
    { USB_DEVICE( 0x1234, 0x0002 )},
    { USB_DEVICE( 0x0EEF, 0x0001 )}, 
    { USB_DEVICE( 0x0EEF, 0x0002 )},
    { USB_DEVICE( 0x3823, 0x0001 )},
    { USB_DEVICE( 0x3823, 0x0002 )}
 };
To

 static struct usb_device_id tk_table[] = {
    { USB_DEVICE( 0x1234, 0x0001 )},
    { USB_DEVICE( 0x1234, 0x0002 )},
    { USB_DEVICE( 0x0EEF, 0x0001 )}, 
    { USB_DEVICE( 0x0EEF, 0x0002 )},
    { USB_DEVICE( 0x3823, 0x0001 )},
    { USB_DEVICE( 0x3823, 0x0002 )},
    {0}
 };

(in other words, add a comma after the existing last line of the table, then a new line, then {0}.)

This will allow the file to compile.

---

### Post by N0YKG on 2008-12-09
Additional information:

You don't need to use their kernel driver - use their X driver (egalax_drv.so) and configure it to use the standard kernel HID device. Copy egalax_drv.so over to /usr/lib/xorg/modules/input, then add the following section to your xorg.conf:

Section "InputDevice"
   Identifier "Egalax"
   Driver     "egalax" 
   Option     "Device"     "usbauto"
   Option     "Parameters" "/var/lib/egalax.cal"
   Option     "ScreenNo"   "0"
   Option     "SendCoreEvents" "true"
EndSection

and add the following to your ServerLayout section:
    InputDevice    "Egalax"

and that should get it working.

---

### Post by quinnteq on 2008-12-09
Thank you so much for replying. Ill give that a shot, thank you so much.

---

### Post by quinnteq on 2008-12-10
I keep getting errors that says I can only run in low graphics mode... I dont know what i did wrong... I copied everything exactly... and moved the driver to the correct folder... 

Please, Let me know what to send next to figure out whats wrong now... thanks so much in advance!

---

### Post by quinnteq on 2008-12-10
I keep getting an error saying I can only start up in "Low Graphics Mode" and the touch screen isnt registered at all. Whats the next step in fixing this? I copied everything exactly... I dont understand why. Please let me know what else to post in order to solve this. Thank you so much!

---

### Post by quinnteq on 2008-12-10
sorry i posted twice, i got an error the first time saying that the server was down or something...

---

### Post by quinnteq on 2008-12-14
*bump*

---

### Post by Sullr on 2008-12-14
Hi,

I am having the same problem you are, but I also tried the beta driver which automates everything for you, everything looks good except the touch is not working at all and when I look at xorg.conf it is missing

```
Section "ServerLayout"
InputDevice "EETI" "SendCoreEvents"
```

Soon as I add that and reboot I get the message about running in low graphics mode!!!!

The guide also talks about adding lines to xorg.conf for mouse so you do not get weird double click events, but again any time I add anything to xorg.conf I cannot boot as I get the low graphics mode message.

This is what my xorg.conf looks like after I have ran the automated beta driver "setup.sh" I can also confirm it does place "egalax_drv.so" in the correct spot!

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
### Touch Configuration Beginning ###
Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection
### Touch Configuration End ###
```

I am running Ubuntu 8.10 kernel  2.6.27-9.

---

### Post by quinnteq on 2008-12-15
Yea. I am getting the same errors... I dont know what to make of it. I tried the beta one as well... Maybe there is a compatibility issue of the NEW driver with the X server (seeing as its beta... but I dont know...) ... could try using the old driver (replace the driver in the /lib/modules folder in X11 or somthing) and use the same config...minus the path change in the xorg.conf file to point to the OLD driver instead of the NEW one.

I got it to work once not using this method... and it was working just great.. but then i rebooted a few times (regular use, no updates or anything) and it died. saying Ubuntu must load up in low graphics mode, and no touch screen.

So lets try using the new script, but replace the new driver with the old one and change the xorg.conf to reflect that change... when i get the chance to look at the machine i have in question here, ill post back. Let me know how it works for you.

Basically what i propose to do is this...

1) run the new script... reboot, and have it load up in low graphics mode

2) replace the new driver with the old one (hopefully the problem doesnt lie in the way the script lays out the xorg configuration) and using the old driver in the new automated script installation, maybe this could work.

3)reboot... and cross your fingers.

EDIT: 

Oh... I also just thought. Maybe deleting all the information about other input devices (mice and the like, excludeing the keyboard) in the xorg.conf file may fix the issue too... maybe its a conflict between input devices. I dont need them as the main device will be the touch screen as its for a Digital Picture Frame and it doesnt need a keyboard.

---

### Post by rburhum on 2010-04-14
Did you guys ever figure this one out?

---

