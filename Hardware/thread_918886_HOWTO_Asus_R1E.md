---
title: "HOWTO Asus R1E"
date: 2008-09-13
forum: Hardware
---

### Post by Zeyelth on 2008-09-13
I've written a [HOWTO on the Asus R1E Tablet PC](https://help.ubuntu.com/community/AsusR1E).

This thread is intended for feedback and general discussion around the HOWTO and the Asus R1E, although users of the Asus R1F may want to give it a try too, as the tablet feature supposedly uses the same hardware.

I know there is a specific forum for HOWTOs, but since this one is mainly intended to troubleshoot and fix issues with this specific laptop/Tablet PC, I figured this is a better place to post it.

Currently, the HOWTO only deals with the tablet feature, as mostly everything else works to some degree, and a lot of issues will most likely be solved in Ubuntu 8.10. As a result, I will probably not do any major updates to the HOWTO before then.

I should point out that I've written most of the HOWTO from memory, so it's quite likely that I've omitted required steps. If anyone decides to make use of this HOWTO, please post feedback, comments and criticism here, so that it can be improved. :)

**Updated:** Added section which explains how to enable the "rotate screen" button as well as the auto-rotate screen when switching to "tablet mode".
**Updated:** Added sections for Ubuntu 8.10.
**Updated:** Added sections for Ubuntu 10.04.

---

### Post by mkongsfelt on 2008-10-06
I get some errors when using the command "make" (On an Asus R1F):

mikkel@mikkel-tablet:~/linuxwacom-0.8.1-4$ make
Making all in src
make[1]: Entering directory `/home/mikkel/linuxwacom-0.8.1-4/src'
Making all in .
make[2]: Entering directory `/home/mikkel/linuxwacom-0.8.1-4/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/mikkel/linuxwacom-0.8.1-4/src'
Making all in wacomxi
make[2]: Entering directory `/home/mikkel/linuxwacom-0.8.1-4/src/wacomxi'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mikkel/linuxwacom-0.8.1-4/src/wacomxi'
Making all in util
make[2]: Entering directory `/home/mikkel/linuxwacom-0.8.1-4/src/util'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \
	then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
In file included from wacomcfg.c:35:
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory
In file included from wacomcfg.h:27,
                 from wacomcfg.c:35:
/usr/include/X11/extensions/XInput.h:182: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:214: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:247: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:277: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:305: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:344: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:397: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:418: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:442: error: expected specifier-qualifier-list before 'Bool'
/usr/include/X11/extensions/XInput.h:463: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:473: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:490: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:503: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:516: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:529: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:542: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:554: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:564: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:577: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:595: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:607: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:618: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:631: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:646: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:651: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:659: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:668: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:681: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:692: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:698: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:705: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:726: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:735: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:750: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:764: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:785: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:812: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:827: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:839: error: expected specifier-qualifier-list before 'Time'
/usr/include/X11/extensions/XInput.h:852: error: expected specifier-qualifier-list before 'XID'
/usr/include/X11/extensions/XInput.h:910: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'extern'
/usr/include/X11/extensions/XInput.h:916: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:923: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:935: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:941: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:955: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:964: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:978: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:987: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:994: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1002: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1010: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1020: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1027: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1034: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/usr/include/X11/extensions/XInput.h:1047: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1055: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
/usr/include/X11/extensions/XInput.h:1061: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1067: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1074: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1081: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1090: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1095: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1104: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1109: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1114: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1120: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1128: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1134: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1141: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1148: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1157: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1165: error: expected ')' before '*' token
/usr/include/X11/extensions/XInput.h:1170: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'XSendExtensionEvent'
/usr/include/X11/extensions/XInput.h:1181: error: expected ')' before '*' token
In file included from /usr/include/X11/Xproto.h:76,
                 from /usr/include/X11/extensions/XIproto.h:53,
                 from wacomcfg.h:28,
                 from wacomcfg.c:35:
/usr/include/X11/Xmd.h:137: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'typedef'
In file included from /usr/include/X11/extensions/XIproto.h:53,
                 from wacomcfg.h:28,
                 from wacomcfg.c:35:
/usr/include/X11/Xproto.h:656: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/Xproto.h:1187: error: expected specifier-qualifier-list before 'INT32'
In file included from wacomcfg.h:28,
                 from wacomcfg.c:35:
/usr/include/X11/extensions/XIproto.h:811: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/extensions/XIproto.h:919: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/extensions/XIproto.h:1297: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/extensions/XIproto.h:1379: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/extensions/XIproto.h:1394: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/extensions/XIproto.h:1432: error: expected specifier-qualifier-list before 'INT32'
/usr/include/X11/extensions/XIproto.h:1513: error: expected specifier-qualifier-list before 'INT32'
In file included from wacomcfg.c:35:
wacomcfg.h:58: error: expected specifier-qualifier-list before 'Display'
wacomcfg.h:62: warning: struct has no members
wacomcfg.h:75: error: expected ')' before '*' token
wacomcfg.c: In function 'CfgError':
wacomcfg.c:71: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c:72: error: 'WACOMCONFIG' has no member named 'pfnError'
wacomcfg.c: In function 'CfgGetDevs':
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:82: warning: implicit declaration of function 'XListInputDevices'
wacomcfg.c:82: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:83: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:85: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c: At top level:
wacomcfg.c:95: error: expected ')' before '*' token
wacomcfg.c: In function 'WacomConfigListDevices':
wacomcfg.c:145: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:155: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:157: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:161: error: 'XDeviceInfo' has no member named 'use'
wacomcfg.c:161: error: 'XDeviceInfo' has no member named 'use'
wacomcfg.c:162: error: 'XDeviceInfo' has no member named 'use'
wacomcfg.c:165: error: 'XDeviceInfo' has no member named 'num_classes'
wacomcfg.c:167: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:181: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:183: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:188: error: 'XDeviceInfo' has no member named 'use'
wacomcfg.c:188: error: 'XDeviceInfo' has no member named 'use'
wacomcfg.c:189: error: 'XDeviceInfo' has no member named 'use'
wacomcfg.c:192: error: 'XDeviceInfo' has no member named 'num_classes'
wacomcfg.c:194: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:196: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c: In function 'WacomConfigOpenDevice':
wacomcfg.c:307: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:311: error: 'WACOMCONFIG' has no member named 'nDevCnt'
wacomcfg.c:313: error: 'WACOMCONFIG' has no member named 'pDevs'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'name'
wacomcfg.c:314: error: 'XDeviceInfo' has no member named 'num_classes'
wacomcfg.c:326: warning: implicit declaration of function 'XOpenDevice'
wacomcfg.c:326: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:326: error: 'XDeviceInfo' has no member named 'id'
wacomcfg.c:326: warning: assignment makes pointer from integer without a cast
wacomcfg.c: In function 'WacomConfigCloseDevice':
wacomcfg.c:348: warning: implicit declaration of function 'XFree'
wacomcfg.c: In function 'WacomConfigSetRawParam':
wacomcfg.c:364: error: 'XDeviceResolutionControl' has no member named 'control'
wacomcfg.c:365: error: 'XDeviceResolutionControl' has no member named 'length'
wacomcfg.c:366: error: 'XDeviceResolutionControl' has no member named 'first_valuator'
wacomcfg.c:367: error: 'XDeviceResolutionControl' has no member named 'num_valuators'
wacomcfg.c:368: error: 'XDeviceResolutionControl' has no member named 'resolutions'
wacomcfg.c:370: warning: implicit declaration of function 'XChangeDeviceControl'
wacomcfg.c:370: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:384: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:396: warning: implicit declaration of function 'XSetDeviceMode'
wacomcfg.c:396: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c: In function 'WacomConfigGetRawParam':
wacomcfg.c:412: error: 'XDeviceResolutionControl' has no member named 'control'
wacomcfg.c:413: error: 'XDeviceResolutionControl' has no member named 'length'
wacomcfg.c:414: error: 'XDeviceResolutionControl' has no member named 'first_valuator'
wacomcfg.c:415: error: 'XDeviceResolutionControl' has no member named 'num_valuators'
wacomcfg.c:416: error: 'XDeviceResolutionControl' has no member named 'resolutions'
wacomcfg.c:418: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:427: warning: implicit declaration of function 'XGetDeviceControl'
wacomcfg.c:427: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:433: error: 'XDeviceResolutionState' has no member named 'resolutions'
wacomcfg.c:433: error: 'XDeviceResolutionState' has no member named 'num_valuators'
wacomcfg.c:442: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:452: error: 'WACOMCONFIG' has no member named 'pDisp'
wacomcfg.c:457: error: 'XDeviceResolutionState' has no member named 'resolutions'
wacomcfg.c:457: error: 'XDeviceResolutionState' has no member named 'num_valuators'
wacomcfg.c:458: error: 'XDeviceResolutionState' has no member named 'resolutions'
wacomcfg.c:458: error: 'XDeviceResolutionState' has no member named 'num_valuators'
wacomcfg.c:464: error: 'WACOMCONFIG' has no member named 'pDisp'
make[2]: *** [wacomcfg.lo] Error 1
make[2]: Leaving directory `/home/mikkel/linuxwacom-0.8.1-4/src/util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mikkel/linuxwacom-0.8.1-4/src'
make: *** [all-recursive] Error 1

---

### Post by Zeyelth on 2008-10-07
Looks like you're missing a package. Probably "libx11-dev". Install it via your fav. package manager and try again. I'll add it to the list.

---

### Post by mkongsfelt on 2008-10-08
Thanks. It turned out that i also needed libXi-dev, so might add that one as well.

But still... now i get this error when trying to load the driver:
mikkel@mikkel-tablet:~/linuxwacom-0.8.1-4$ sudo rmmod wacom
ERROR: Module wacom does not exist in /proc/modules

I am not quite sure what files i need to copy to /proc/modules

---

### Post by Zeyelth on 2008-10-08
I'll update it later.

The rmmod command is only to make sure you remove the old module (driver). You should be able to ignore that error message. If you've installed the module try rebooting and see if it reacts to the pen. If so, you just need to fix the xorg.conf. If it doesn't respond, make sure it's installed properly.

---

### Post by mkongsfelt on 2008-10-08
Thank you very much for a good guide! It works perfectly now.

---

### Post by Zeyelth on 2008-10-09
You're welcome. :)

---

### Post by goldenfly on 2009-01-09
First of all, I would like to thank Zeyelth for the amazing guide. After following your steps (and a bit of tinkering), I was able to obtain my ASUS R1F tablet functionality running on 8.10. Here are those additional tinkerings:

- The GIMP configuration is not located at:
File->Preferences->Input Devices->Configure Extended Input Devices...

But rather at:
Edit->Preferences->Input Devices->Configure Extended Input Devices...

I'm using GIMP 2.6.1, which came with 8.10

- after configuring the extended input devices in GIMP, I had to click on the button "Save Input Device Settings Now" and then restart GIMP. Also, initially the eraser didn't work, but I fixed it by turning down the brightness level one notch down from 100% and then manually selected the eraser tool. After that, GIMP would automatically toggle between pen and eraser in the correct manner.

- the first time I tried rotating the screen, the pen orientation was flipped (i.e. CCW instead of CW). Subsequently, none of the screen orientation changes updated the pen orientation anymore (both after rotating the screen physically and after pressing the "rotate screen" button). When I looked into this matter, I found out that xsetwacom returned an error saying that libwacomcfg.so.0 could not be found. I fixed it as follows:

sudo cp /usr/local/lib/libwacomcfg.so.0 /usr/lib
sudo ldconfig

Now everything works!!!

Once again, thank you Zeyelth!


MiMiC

---

### Post by Zeyelth on 2010-07-24
Thread revival!

Updated the HOWTO with sections for Ubuntu 10.04 dealing with the rotate screen issues. Basically all that needs to be done is to update the rotatescreen.sh script found under /etc/acpi so that the tablet coordinates rotate as well. Attached a patch I wrote which attempts to figure out the Wacom device names on the system and rotates each of them according to the orientation. Works for me on my R1E. Hopefully it's generic enough to work on any tablet PC out there.

**I haven't done any extensive testing, so use at your own risk.**

To patch the script, download and rename it to "rotatescreen.patch" (the forum wouldn't accept the .patch extension), then run:
```

sudo patch -p0 -i rotatescreen.patch

```

---

### Post by sanosuke.502 on 2012-02-24
It used to work for Ubuntu 9.04, and 10.04 but after ubuntu 10.10 screen wont rotate as far i've seen is that when i run Xinput list in terminal the rotation is activated but the coordinates wont rotate. :( if you have any idea on how to fix this i'll be really thankfull here's my xinput list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen stylus               	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen eraser               	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

---

### Post by Favux on 2012-02-24
Hi sanosuke.502,

We almost figured it out on this thread:  [http://ubuntuforums.org/showthread.php?t=1905861&highlight=Asus+R1E&page=2](http://ubuntuforums.org/showthread.php?t=1905861&highlight=Asus+R1E&page=2)

---

### Post by sanosuke.502 on 2012-02-24
So what should i do first??? do the rotation how to guide??

---

### Post by Favux on 2012-02-24
I was thinking you could try your luck on the modified script in post #13:
```
#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed
#
# xrandr v.s. xsetwacom rotation values:
# "normal":"none", "left":"ccw", "inverted":"half", "right":"cw"

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
#        right)
	inverted)
	NEW_ROTATION="normal"
        WACOM_ROTATION="none"
	;;
	*)
#        NEW_ROTATION="right"
	NEW_ROTATION="inverted"
#        WACOM_ROTATION="cw"
        WACOM_ROTATION="half"
	;;
esac

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
            xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate $WACOM_ROTATION
	fi
done
```
Since it almost seemed to work for him.  He might have been having a hardware problem or something.

But sure, you could just ignore the script already there and use an method 1 script instead.  Definitely a simpler way to go.

---

### Post by sanosuke.502 on 2012-02-24
i think its working but jmmm i need to have it portrait when it rotates because it rotates inverted, wut to do???

---

### Post by Favux on 2012-02-24
Great!  I hope so.

See the part where it says?
```
#        NEW_ROTATION="right"
	NEW_ROTATION="inverted"
#        WACOM_ROTATION="cw"
        WACOM_ROTATION="half"
```
Swap the comments like so:
```
        NEW_ROTATION="right"
#	NEW_ROTATION="inverted"
        WACOM_ROTATION="cw"
#        WACOM_ROTATION="half"
```

---

### Post by sanosuke.502 on 2012-02-24
Ok got it working, here's the final script made some simple mods, the ting is it will only rotate if terminal is open and xinput list is typed first :S and sry i don't know how to put those frames :S


#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

if [ -f /var/lib/acpi-support/screen-rotation ] ; then
  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
fi

case "$ROTATION" in
       right)
#	inverted)
	NEW_ROTATION="normal"
        WACOM_ROTATION="none"
	;;
	*)
        NEW_ROTATION="right"
#	NEW_ROTATION="inverted"
        WACOM_ROTATION="ccw"
#       WACOM_ROTATION="half"
	;;
esac


for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
            xsetwacom set "Wacom ISDv4 90 Pen stylus" rotate $WACOM_ROTATION
	fi
done

---

### Post by sanosuke.502 on 2012-02-24
actually it just needs to have terminal open to work i really don't know why, but if i close terminal it stops auto rotating :S

---

### Post by Favux on 2012-02-24
If you change:
```
#!/bin/sh
```
to:
```
#!/bin/bash
```
Does it work with the terminal closed?

Did you check to see if the script is executable?

---

### Post by sanosuke.502 on 2012-02-24
Nop, still not working with terminal closed

---

### Post by Favux on 2012-02-24
Hmmm.  That's not making much sense to me.

It's executable and using bash instead of sh doesn't help anything.

Ahh.  Since it needs to be running I bet it needs to be autostarted.  Try adding it to 'Startup Applications' and then either log out and back in or restart.  See if that does the trick.

---

### Post by sanosuke.502 on 2012-02-24
how to do that? sry i'm kinda new

---

### Post by Favux on 2012-02-24
Which release are you using?  In Oneiric (or Natty) just click on the Dash Home and type 'Startup Applications'.  Click on that when it shows up and then on Add.  For a name call it Asus Auto-rotation script or something.  Then in command type the directory path to it, which I assume is:
```
/etc/acpi/rotatescreen.sh
```
and click Add.

---

### Post by sanosuke.502 on 2012-02-24
done, but aint working, still terminal dependant, i'm using ubuntu 11.10, CD version

---

### Post by Favux on 2012-02-24
When you navigate to the script in the Nautilus file manager and right click on it and chose Properties in the Permissions tab is the box to allow it as an executable program checked?

---

### Post by sanosuke.502 on 2012-02-24
Nautilus says i don't have permision to change the settings :S how to get the priviledges without terminal???

---

### Post by sanosuke.502 on 2012-02-24
been checking and i don't have nautilus :S, and im not the owner of the file so i can't change the permissions, still googleing for the how to be owner

---

### Post by sanosuke.502 on 2012-02-24
done, allowed to execute the file but aint working :'(

---

### Post by Favux on 2012-02-24
I wouldn't have placed the script in a system directory.  Because it is there you have to be root which makes it a little harder to work with.

So either start Nautilus as root:
```
gskudo Nautilus
```
But be sure to just change it to executable and close the root Nautilus right away or you can mess things up with it.

Or you can do it from the command line.  Change directories to the folder that has the script:
```
cd /etc/acpi
```
The use sudo to become root for the command:
```
sudo chmod +x rotatescreen.sh
```

---

### Post by Favux on 2012-02-24
Well shoot.  What is the problem?  I appear to missing the obvious. :confused:

You restarted?

---

### Post by sanosuke.502 on 2012-02-24
yes i restarted it, and tried on a live USB of linux mint 12 but still rotation is terminal dependant, this is weird lol XD i don't know wut terminal has that makes it work

---

### Post by Favux on 2012-02-24
Could I clarify something?  Do you have Ubuntu 11.10 installed on the hard driver or are you running it from a CD or USB stick?

---

### Post by sanosuke.502 on 2012-02-24
installed on my HDD, just wanted to give it a try with the mint live usb stick, im using the Gnome version should i try with a KDE??? or there's a way to make it work??

---

### Post by Favux on 2012-02-24
Alright.  Well it won't work on USB stick because you would have to actually change the files.

At this point I'm throwing in the towel.  You should probably try a method one script on the Rotation HOW TO.  In the meantime whatever I'm missing might smack me in the face.

---

### Post by sanosuke.502 on 2012-02-24
ok i'm gonna put terminal in startup lol, that will do for my First Aid Step 1 USMLE studying. thanks for all the help

---

### Post by Favux on 2012-02-25
Good luck on the USMLE!  :)

---

### Post by Zeyelth on 2012-02-28
I'm still running 10.04 on my R1E. Will wait until 12.04 before reinstalling, though I'm likely to switch to Mint due to Unity.

If I run into any issues after I've upgraded, I'll update the guide.

---

### Post by sanosuke.502 on 2012-03-14
thanks XD

---

### Post by sanosuke.502 on 2012-06-24
hey how's it going have you guys tried on the new 12.04 version???

---

