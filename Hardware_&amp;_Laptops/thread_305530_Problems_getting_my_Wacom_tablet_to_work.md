---
title: "Problems getting my Wacom tablet to work"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by Jcarr_toonist on 2006-11-23
HI,

I can't get my Wacom tablet to work. I've installed the driver and edited my xorg.conf file this is what it looks like now...

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "InputDevice"

	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/ttyS1"             # Change to 
	Option	    "Type" "stylus"
# 	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY

EndSection

Section "InputDevice"

	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/ttyS1"          # Change to 
	Option	    "Type" "eraser"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY

EndSection

Section "InputDevice"
                                                  
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/ttyS1"          # Change to 
	Option	    "Type" "cursor"
# 	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY

EndSection

I got the /dev/ttyS1 from running wacdump which looks like this....

> MODEL=Wacom ArtPadII 4x5                ROM=1.3-3
CLS=Serial  VNDR=Wacom  DEV=ArtPadII  SUB=KT-0405-R

A0 13 4F 00 23 13 00                                        ..O.#..


TOOLTYPE=NONE                            IN_PROX=out
  BUTTON=+00000 (+00000 .. +00000)         POS_X=+00000 (+00000 .. +06400)
   POS_Y=+00000 (+00000 .. +04800)      PRESSURE=+00000 (+00000 .. +00255)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=
     BT8=                BT9=               BT10=               BT11=
    BT12=               BT13=               BT14=               BT15=
    BT16=               BT17=               BT18=               BT19=
    BT20=               BT21=               BT22=               BT23=

and inside wacdump the tablet seems to work as the numbers change and what not when I move the stylus across the tablet. 

But anywhere else the tablet doesn't do anything. In gimp I tried 'configure extended input devices' and none where found. 

thanks in advance

---

