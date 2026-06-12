---
title: "Wacom DigitizerII 12x18 UD1218R Problems with Maverick Server"
date: 2010-12-20
forum: Hardware
---

### Post by dreh on 2010-12-20
Hi,
i'm having trouble with my Wacom tablet. Its attached over serial cable. I used this tutorial [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1) .

**wacdump /dev/ttyS0 sees the tablet and values are changing drawing on it:**
MODEL=Wacom DigitizerII 12x18           ROM=1.4-2
CLS=Serial  VNDR=Wacom  DEV=Digitizer II  SUB=UD-1218-R
A0 51 5E 04 59 1C 00 25 08                                  .Q^.Y..%.
TOOLTYPE=PEN                             IN_PROX=in 

**/usr/share/X11/xorg.conf.d/50-wacom.conf**
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Option "Device" "/dev/ttyS0"          # SERIAL ONLY
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Do I need the server section as described in [http://linuxwacom.sourceforge.net/index.php/howto/srvlayout](http://linuxwacom.sourceforge.net/index.php/howto/srvlayout)?

Tried several different settings the mileage is between GDM ist starting up, keyboard and mouse is dead, ... every approach never brought up the tablet.

xserver-xorg-input-wacom 10.8-ubuntu is installed 
xserver 1.9
uname -r 2.6.35-23-server
AMD SMP x86_64

ty - dreh

---

### Post by Favux on 2010-12-20
Hi dreh,

Welcome to Ubuntu forums!

It's not the "ServerLayout".  See "Notice for Serial Graphics Tablet Users" in red near the top of the HOW TO you linked.  It links to the patches and instructions you need.

The serial patches only work up to and including xf86-input-wacom 0.10.6.  As you see thorwil figured out how to get the patched 0.10.6 to compile in Maverick, overcoming the last obstacle.

Meanwhile we hope someone will take up developing the serial patch further.  Peter gave big hints and pointers as to what he would accept into xf86-input-wacom.

Good luck!

---

### Post by dreh on 2010-12-20
Hi Favux,
ty for your warm welcome and your fast answer.
I tried the tutorial again. I can't get it run. This is what I did:

1. uninstalled xserver-xorg-input-wacom via synaptic
2. sudo rmmod wacom
3. git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom. As far as I understood the patch is already integraded in wcmCommon.c. or am I wrong?
4. ./autogen.sh --prefix=/usr
5. make & sudo make install
6. ./autogen.sh --prefix=/usr --libdir=/usr/lib64 I did this cause I have evdev_drv.so in both locations - just to be sure + make make install
7. gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device"		"/dev/ttyS0"
	Option "Type"		"stylus"
	Option "ForceDevice"	"ISDV4"	
EndSection

Is this right: The wacom.ko is not necessary for serial tablets? So I can ignore it?

Which Syntax is the right one or what is the difference between Section "InputDevice" and Section "InputClass".

The tutorial is a bit complicated, (English is not my mother language), so could you point me the right direction.
Ty for your help !
dreh

---

### Post by Favux on 2010-12-20
Hi dreh,

> 1. uninstalled xserver-xorg-input-wacom via synaptic
Don't, there is a new dependency xserver-xorg-input-all which will also be uninstalled and you need it installed.  It's necessary.  So reinstall.
> 3. git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom. As far as I understood the patch is already integraded in wcmCommon.c. or am I wrong?
The patch is not in xf86-input-wacom 0.10.10+.  Peter declined to accept it, it needed more work.  He gave a long, detailed critique/guideline of what was needed after the second patch attempt.  The guy working on it stopped after his second attempt.  Other things to do I guess.  The second patch (the improved version) will only work on 0.10.6.  So you have to download the tar:  [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)  (all packages).  Patch it.  Then you have to do the patch so 0.10.6 will compile in Maverick.
> 4. ./autogen.sh --prefix=/usr
With the tar it'll be:
```
./configure --prefix=/usr
```
I don't know about the 64-bit flag on your system.
> Option "ForceDevice" "ISDV4"
Remove, it's for tablet pc's.  In fact in the recent versions of xf86 it's been deprecated for them too.  If anything you'd need something like:
```
Option "ForceDevice" "Serial"
```
So it should look something like:
```
Section "InputClass"
    Identifier "Wacom serial tablet class"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
#    Option "ForceDevice" "Serial"  # ?
EndSection
```
"InputClass" is for .conf files.  We'd have to see if there were any other matches we could do.
> Is this right: The wacom.ko is not necessary for serial tablets? So I can ignore it?
Yes, the wacom.ko is the usb kernel driver.  Your serial tablet does not need it.

---

### Post by dreh on 2010-12-21
**Hi Favux,**
ty for your help.
I patched and compiled .. installed. nice.

Unfortunately its still not working: 
**less /var/log/Xorg.0.log**

```
My 18473.695] (II) LoadModule: "wacom"
[ 18473.695] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 18473.695] (II) Module wacom: vendor="X.Org Foundation"
[ 18473.695]    compiled for 1.8.99.905, module version = 0.10.8
[ 18473.695]    Module class: X.Org XInput Driver
[ 18473.695]    ABI class: X.Org XInput driver, version 11.0
[...]
 18473.873] (**) Option "Device" "/dev/ttyS0"
[ 18473.874] (**) Option "BaudRate" "38400"
[ 18473.874] (**) Option "StopBits" "1"
[ 18473.874] (**) Option "DataBits" "8"
[ 18473.874] (**) Option "Parity" "None"
[ 18473.874] (**) Option "Vmin" "1"
[ 18473.874] (**) Option "Vtime" "10"
[ 18473.874] (**) Option "FlowControl" "Xoff"
[ 18473.874] (**) Option "SendCoreEvents"
[ 18473.874] (**) stylus: always reports core events
[ 18477.127] (WW) stylus: Waited too long for answer (failed after 3 tries).
[ 18477.127] (WW) stylus: Query failed with 38400 baud. Trying 19200.
[ 18480.381] (WW) stylus: Waited too long for answer (failed after 3 tries).
[ 18483.634] (WW) stylus: Waited too long for answer (failed after 3 tries).
[ 18483.634] (II) stylus: serial tablet id 0x90.
[ 18483.635] (II) UnloadModule: "wacom"
[ 18483.635] (EE) PreInit returned NULL for "stylus"
[ 18483.635] (**) Option "Device" "/dev/input/wacom"
[ 18483.635] (EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
[ 18483.635] (EE) eraser: Error opening /dev/input/wacom (No such file or directory)
[ 18483.635] (II) UnloadModule: "wacom"
```

**This is my config:**

```

Section "ServerLayout"
  Identifier    "Default Layout"
##  Screen        "Default Screen"0.10.
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
EndSection

Section "InputClass"
    Identifier "Wacom serial tablet class"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"  # ?
EndSection

Section "InputDevice"
  Driver        "wacom"0.10.
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
  Option	"BaudRate"	"38400"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"0.10.
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
  Option        "BaudRate"      "38400"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
  Option        "BaudRate"      "38400"
EndSection

```
Any clues why it's not working. I tested different Baud Rate didn't change anything. The module says its version 0.10.8 shouldn't it say 0.10.6 (patched driver)?
Ty dreh

---

### Post by Favux on 2010-12-21
Good, progress!

This would be a serial snippet for 50-wacom.conf in /usr/share/X11/xorg.conf.d/.  I thought you were going to use it.  If you are using xorg.conf you don't need to worry about it.  I don't think any of the serial snippets will match your tablet so you don't have to deactivate them.  You want to use either xorg.conf or 50-wacom.conf.  Not both.  So remove it from xorg.conf.
```
Section "InputClass"
    Identifier "Wacom serial tablet class"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"  # ?
EndSection
```
Also starting with X server 1.7 "SendCoreEvents" is deprecated (no longer used).  And unless you have a Wacom tablet mouse you do not need the cursor section.  So it would look something like:
```
Section "ServerLayout"
  Identifier    "Default Layout"
##  Screen        "Default Screen"0.10.
  InputDevice   "stylus"
  InputDevice   "eraser"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
  Option	"BaudRate"	"38400"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"0.10.
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
  Option        "BaudRate"      "38400"
EndSection
```
Do you know what the baudrate of the tablet is suppose to be?  I vaguely remember reading the old serial code.  I think the allowed baudrates were 2400, 4800, 9600, 14,400 ? and ?  I guess I don't remember for sure. Also try without the Option:
```
  Option        "ForceDevice"   "SERIAL"
```
> The module says its version 0.10.8 shouldn't it say 0.10.6 (patched driver)?
That worries me too.  Maybe something new to 0.10.8 that 0.10.6 didn't over write?  I don't think thorwil mentioned it.

---

### Post by dreh on 2010-12-21
Ok I found out the patched driver was installed in the old place.

/usr/**local**/lib/xorg/modules/input/

instead of 

usr/lib/xorg/modules/input/

now xorg is loading the proper 10.6 (patched)
Module wacom: vendor="X.Org Foundation"
[  4477.981]    compiled for 1.9.0, module version = 0.10.6
[  4477.981]    Module class: X.Org XInput Driver
[  4477.981]    ABI class: X.Org XInput driver, version 11.0

for some reason /usr/share/X11/xorg.conf gets totally ignored so I use /usr/share/X11/xorg.conf.d/50-wacom.conf

```
Section "ServerLayout"
  Identifier    "Default Layout"
##  Screen        "Default Screen"0.10.
  InputDevice   "stylus"
  InputDevice   "eraser"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
#  Option       "BaudRate"      "38400"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
#  Option        "Device"        "/dev/input/wacom"0.10.
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "SERIAL"           # Tablet PC ONLY
#  Option        "BaudRate"      "38400"
EndSection
```

if I uncomment the Screen option the Xserver doesn't boot.
Option        "ForceDevice"   "SERIAL" -> makes no difference
Option        "BaudRate"      "38400" -> seems like correct speed is detected automatically

Xorg log gives this

```
[  4478.184] (**) Option "Device" "/dev/ttyS0"
[  4478.184] (**) stylus: always reports core events
[  4478.185] (**) Option "BaudRate" "9600"
[  4478.185] (**) stylus: serial speed 9600
[  4478.185] (II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
[  4478.185] (**) Option "StopBits" "1"
[  4478.185] (**) Option "DataBits" "8"
[  4478.185] (**) Option "Parity" "None"
[  4478.185] (**) Option "Vmin" "1"
[  4478.185] (**) Option "Vtime" "10"
[  4478.185] (**) Option "FlowControl" "Xoff"
[  4478.185] , 0x24, 0x23, 0x24, 0x23, 0x24, 0x53, 0x50, 0xd, 0x23, 0xd(==) Wacom tablet model : UD-1218-R00 V1.4-2
[  4480.151] , 0x52, 0xd, 0x43, 0xd(--) stylus: using pressure threshold of 27 for button 1
[  4482.223] (--) stylus: Wacom Serial UD tablet speed=9600 maxX=22860 maxY=15240 maxZ=255 resX=1270 resY=1270  tilt=disabled
[  4482.223] , 0x54, 0xd(--) stylus: top X=0 top Y=0 bottom X=22860 bottom Y=15240 resol X=1270 resol Y=1270
[  4482.225] (**) Option "Device" "/dev/ttyS0"
[  4482.225] (**) eraser: always reports core events
[  4482.225] (**) Option "BaudRate" "9600"
[  4482.225] (**) eraser: serial speed 9600
[  4482.225] (II) XINPUT: Adding extended input device "eraser" (type: ERASER)
[  4482.226] (--) eraser: top X=0 top Y=0 bottom X=22860 bottom Y=15240 resol X=1270 resol Y=1270
```

everything looks good in my opinion - but tablet is still not responding. any ideas ?
Ty dreh

---

### Post by dreh on 2010-12-21
xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; stylus                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; eraser                                  	id=7	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Digital Media Pro Keyboard	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Digital Media Pro Keyboard	id=10	[slave  keyboard (3)]

---

### Post by dreh on 2010-12-21
some more debugging infos: I'm wondering why stylus & eraser are XExtensionKeyboard not XExtensionPointer

```
xsetpointer -l2: "Virtual core pointer"	[XPointer]
3: "Virtual core keyboard"	[XKeyboard]
4: "Virtual core XTEST pointer"	[XExtensionPointer]
5: "Virtual core XTEST keyboard"	[XExtensionKeyboard]
6: "stylus"	[XExtensionKeyboard]
7: "eraser"	[XExtensionKeyboard]
8: "Power Button"	[XExtensionKeyboard]
9: "Power Button"	[XExtensionKeyboard]
10: "Microsoft Microsoft® Digital Media Pro Keyboard"	[XExtensionKeyboard]
11: "Microsoft Microsoft® Digital Media Pro Keyboard"	[XExtensionKeyboard]
12: "Logitech USB-PS/2 Optical Mouse"	[XExtensionPointer]

```
```

./xidump -l -v stylus
stylus                         extension
    key: min=8, max=255, num=248
    btn: num=32
    val: axes=6 mode=abs buf=256
    axis[0]: res=1270, min=0, max=22860
    axis[1]: res=1270, min=0, max=15240
    axis[2]: res=1, min=0, max=2048
    axis[3]: res=1, min=-64, max=63
    axis[4]: res=1, min=-64, max=63
    axis[5]: res=1, min=0, max=1023
```
[B]./xidump -u raw stylus ->> nothing 
./xidump stylus ->> nothing[/B]
./wacdump /dev/ttyS0 seems to bring some messages. Interestingly the Mouse pointer goes mayhem till I quit the terminal.

---

### Post by Favux on 2010-12-21
Hi Ty dreh,

Looks like excellent progress!

There is some confusion about xorg.conf and 50-wacom.conf.  xorg.conf should still be in the old location:
```
/etc/X11/xorg.conf
```
Depending on your video chipset driver you may not even have an xorg.conf in /etc/X11 starting with X server 1.7/Lucid (10.04).  You may have to create the xorg.conf file.

50-wacom.conf is the new udev configuration file that allows usb hot plugging and is at:
```
/usr/share/X11/xorg.conf.d/50-wacom.conf
```
for Maverick.

So you are putting a xorg.conf in the 50-wacom.conf.  I am surprised it works!  That's why your screen section breaks X.  They have different syntax.  You can consider the .conf files in xorg.conf.d as extensions of xorg.conf, sort of.

I showed you a serial snippet for 50-wacom.conf and a xorg.conf.  Use one or the other.  Not both.  Not xorg.conf in a 50-wacom.conf.  I think I would use the xorg.conf and forget about 50-wacom.conf.  A serial tablet isn't hot plugged.
> Ok I found out the patched driver was installed in the old place.
/usr/local/lib/xorg/modules/input/
Forgot the flag, right?  Good find.  You probably should delete the version in the wrong location if you haven't already.  Seeing the correct 0.10.6 version is reassuring.
> Option "BaudRate" "38400" -> seems like correct speed is detected automatically

Why then is your Xorg.0.log showing?:
> [  4478.185] (**) Option "BaudRate" "9600"
[  4478.185] (**) stylus: serial speed 9600

xinput list looks good.  It is suppose to say [XExtensionKeyboard] if the tablet is on the Wacom driver.  That is what you want to see.

Some of the serial tablets have trouble initializing.  Some serial tablet pc's log out of X and then back in and that often gets their digitizer working.  I have no idea why this works.

I have seen some serial tablets require starting wacdump to initialize.  Again no idea why this works.  So they use a script to start wacdump when they boot to get their tablet going.

---

### Post by dreh on 2010-12-22
It works ... wackycom.

I reconfigured everything in /etc/X11/xorg.conf. It is exactly like you have described it - initialization just works with wacdump /dev/ttyS0. wacdump has to be shutdown immedietly after start otherwise letting it run more than a few seconds will crash the driver somehow. A second start of wacdump will give just an error note and tablet is dead (I have to restart Xserver). But starting it once shutting down fast -> the tablet works!

I had to set the ClickForce to around 80 with xsetwacom -> no more random "mouseclicks". 

I tested in Gimp the pressure everything looks more or less ok.
Xorg.0.log gets spammed with this one for every tablet event

[  5091.514] xf86WcmSerialValidate: bad magic at 2 v=e0 l=7
[  5091.514] xf86WcmSerialValidate: bad magic at 2 v=e0 l=7

Maybe 'cause I set the debbuging level to 255.

Resumee:
Buying a 12x18 tablet for under 20 EUR (around US30$) on ebay is worth it. I'm gonna fine tweak everything and keep you updated. It would be great if someone could patch the driver for serial support with sebastians code. Unfortunatly my skills are to low for that. The patch driver itself seems to work nice running wacdump without X gives smooth proper outputs - just X integration s***s. Gtg now. I'm gonna post all my configs this evening, for archive.

Thank you Favux - without you I would have give up early.

---

### Post by Favux on 2010-12-22
Hi Ty dreh,

Nice work!

You are welcome.  I'm glad you have a working serial tablet in Maverick.

Taking your time to post your working configuration and any updates is greatly appreciated.

---

### Post by dreh on 2011-01-19
update after some time of use:

the initialization process is still very uncomfortable. It needs normally around 3x wacdump and CTRL-C to get the driver initialized. On "Bad Hair Days" the Xserver freezes, even remote login and killing all gdm doesn't help getting it up again - reboot. Since my graphic card also runs with glitches I cant't confirm it's a wacomdriver problem alone - new card is ordered. On some days the tablet works fine, on other days the pen input in gimp is very slow. It takes several seconds till the stroke is on paper. Xsetwacom commands are getting ignored in Xorg.conf maybe cause tablet is not initialized at that time. I have to manually type in the values. I hope there will be a fixed driver soon. 

```

Section "InputDevice"
        Driver        "wacom"
        Identifier    "stylus"
        Option        "Device"        "/dev/ttyS0"
        Option        "Type"          "stylus"
        Option        "ForceDevice"   "SERIAL"
        #Option       "BaudRate"      "9600"
        #Option       "ForceDevice"   "ISDV4"
        #Option       "FlowControl"   "Xon"
        #Option       "DebugLevel"    "255"
        #Option       "Threshold"     "10"
        Option        "ClickForce"    "88"
EndSection

Section "InputDevice"
        Driver        "wacom"
        Identifier    "eraser"
        #Option       "Device"        "/dev/input/wacom"0.10.
        Option        "Device"        "/dev/ttyS0"
        Option        "Type"          "eraser"
        #Option       "ForceDevice"   "SERIAL"
        Option        "BaudRate"      "9600"
EndSection
```
dreh

---

### Post by dreh on 2011-01-31
Hi Favux et al
do you(or anyone else)know if the menu strip is supported. I couldn't find any infos regarding serial menu strip or is this referred to "pad". 
Thank you

---

### Post by Favux on 2011-01-31
Hi dreh,

Actually I'm not sure.  You are correct and the pad is the tablet buttons.  I don't know if the serial tablet menu strips qualify though.  It seems like the LWP doesn't think so.

I know they are buttons from the descriptions.  Can you get a button press and release in xev when you use them?  It's possible a userland app. could be written to support them.  The Waltop tablets may be in a similar place with their tablet hotkeys.

---

