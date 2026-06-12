---
title: "Fine Point Tablet driver Gateway laptop"
date: 2009-02-09
forum: Hardware
---

### Post by jonthemiller on 2009-02-09
I currently have a Gateway M 285-E tablet running 8.04 Hardy GNOME with following hardware specs:
[LIST]
[*]2.0 GHz Core 2 Duo
[*]2 GB RAM
[*]100 GB HDD (2 50 GB partitions)
[*]ATI X1400 Mobility video chipset
[*]Finepoint Tablet
[/LIST]
It uses the Fine Point tablet hardware rather than the much more popular Wacom driver for reasons I can't see. I'm trying to find a definitive guide to getting the tablet installed so I can finally delete my Vista partition, its seriously the only reason I keep Windows around.  Would it be easier to install in a later version of Ubuntu, or better supported in a different distro?  All guides I have read and followed have not worked for me so far, and the only ones I've seen where anyone can get their tablet to work are the M295 model which use the Wacom tablet.  Help?

---

### Post by Favux on 2009-02-09
Hi jonthemiller,

The reason you need the finepoint drivers is that from what you are saying you have the Finepoint Innovations Tablet PC Digitizer.  So the driver you need is called fpit, the line to google with is "xf86-input-fpit driver".

It's home is:

[http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/]("http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/")

There is a deb of 1.2.0-1 at the Debian site, which given the "-1" seems current:

[http://packages.debian.org/sid/xserver-xorg-input-fpit]("http://packages.debian.org/sid/xserver-xorg-input-fpit")

And Synaptic Package Manager has it. Search "fpit" and you get 1:1.2.0-1 build 1. The Synaptic version may be slightly older than the Debian deb. So it's your choice which to install.

Hardy should be fine.  Just install the driver.  And reboot (probably better than restarting X).  Then your xorg.conf probably needs to be configured if you don't get a working stylus after installing the driver.  The only sticking point may be figuring out what format in xorg.conf the finepoint driver wants.

You have a stylus.  Does it have a one side button or more?  Is there an eraser?  Please attach your xorg.conf if you need to.

---

### Post by jonthemiller on 2009-02-09
I installed the .deb of the FPIT driver, I had the older version from Synaptic installed to no avail.  Here is my /etc/X11/xorg.conf:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by Favux on 2009-02-09
Hi jonthemiller,

OK.  Do you have an active or passive pen?  I guess the active pen is the one with a battery.

---

### Post by jonthemiller on 2009-02-09
Yeah, its the active pen with the side button and no eraser.  Like this one:
[http://www.skyline-eng.com/index.cfm?fuseaction=product.display&Product_ID=6548](http://www.skyline-eng.com/index.cfm?fuseaction=product.display&Product_ID=6548)

---

### Post by Favux on 2009-02-09
Hi jonthemiller,

Alright then try the attached xorg.conf.  Be sure to back yours up first.  You should probably compare the two side by side so you can familiarize yourself with the changes.  Then restart.

Hopefully the deb you installed took care of the setserial stuff so we don't have to worry about it.

Another issue you should be aware of.  You have the ATI proprietary driver "fglrx" installed.  Unless you have one of the two latest versions, it does not support rotation.  And even the new ones that do won't support rotation correctly with Compiz.  Xorg's OSS driver "radeon" supports rotation, but again not with Compiz.

---

### Post by jonthemiller on 2009-02-09
Okay, I backed up my old xorg to xorg.conf.old and copied the new one to xorg.conf.  I then restarted and tried to use the pen with no success.  I installed the setserial package and restarted again.  I'm assuming the setserial configs have to happen now.

The rotation issues aren't a problem to me at the moment, if you can get the pen working I'll be happy.

---

### Post by Favux on 2009-02-09
Hi jonthemiller,

Oh well.  It would have been nice if it worked.

So we may have to do the standard hunt for the correct serial port for a serial tablet.  I can offer a few tips.  But first let's try this.

In "/usr/X11R6/lib/modules/input" is there "fpit_drv.o"?

Then in "/etc/serial.conf" try adding "setserial /dev/ttyS3 autoconfig".  Restart.

Any luck?

---

### Post by jonthemiller on 2009-02-09
The only folder in /usr/X11R6/lib is fglrx

---

### Post by Favux on 2009-02-10
Hmmm.  That's where the readme says the driver is suppose to live.  Maybe the deb installs it somewhere else?  The problem is the readme is two years old and is for v. 1.1.0 of the fpit driver.

To find serial output try:
```
dmesg | grep ttyS
```
and
```
ls /dev/ttyS*
```
setserial can interfere with dmesg.

Also do you know how to use xxd? xxd will exit for devices not listed, otherwise CTRL and C to quit. Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc. Bring the pen to the screen an move it around. You know you have the right ttyS* when you see a reaction with an output of characters. That's the ttyS* you want to use in xorg.conf. In a terminal type:
```
xxd /dev/ttyS0
```

The readme says also to check:
```
/proc/ioports
```
and
```
/sys/devices/pnp0/*
```

I'll attach the readme from the source code.

---

### Post by jonthemiller on 2009-02-10
Okay, I'll show what happened command by command.

> **Favux said:**
> Hmmm.  That's where the readme says the driver is suppose to live.  Maybe the deb installs it somewhere else?  The problem is the readme is two years old and is for v. 1.1.0 of the fpit driver.

To find serial output try:
```
dmesg | grep ttyS
```
and
```
ls /dev/ttyS*
```
setserial can interfere with dmesg.

Well, the first one gave this output:
```
[   20.255709]   hash matches device ttyS3
```
and the second gave this:
```
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
```

> **Favux said:**
> Also do you know how to use xxd? xxd will exit for devices not listed, otherwise CTRL and C to quit. Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc. Bring the pen to the screen an move it around. You know you have the right ttyS* when you see a reaction with an output of characters. That's the ttyS* you want to use in xorg.conf. In a terminal type:
```
xxd /dev/ttyS0
```

Each one of those (ttyS0 - ttyS3) gave no output, even with the pen moving around on top of the screen.

> **Favux said:**
> The readme says also to check:
```
/proc/ioports
```
and
```
/sys/devices/pnp0/*
```

I'll attach the readme from the source code.

```
jon@jon-laptop:~$ xxd /proc/ioports
0000000: 3030 3030 2d30 3031 6620 3a20 646d 6131  0000-001f : dma1
0000010: 0a30 3032 302d 3030 3231 203a 2070 6963  .0020-0021 : pic
0000020: 310a 3030 3430 2d30 3034 3320 3a20 7469  1.0040-0043 : ti
0000030: 6d65 7230 0a30 3035 302d 3030 3533 203a  mer0.0050-0053 :
0000040: 2074 696d 6572 310a 3030 3630 2d30 3036   timer1.0060-006
0000050: 6620 3a20 6b65 7962 6f61 7264 0a30 3037  f : keyboard.007
0000060: 302d 3030 3737 203a 2072 7463 0a30 3038  0-0077 : rtc.008
0000070: 302d 3030 3866 203a 2064 6d61 2070 6167  0-008f : dma pag
0000080: 6520 7265 670a 3030 6130 2d30 3061 3120  e reg.00a0-00a1 
0000090: 3a20 7069 6332 0a30 3063 302d 3030 6466  : pic2.00c0-00df
00000a0: 203a 2064 6d61 320a 3030 6630 2d30 3066   : dma2.00f0-00f
00000b0: 6620 3a20 6670 750a 3031 3730 2d30 3137  f : fpu.0170-017
00000c0: 3720 3a20 3030 3030 3a30 303a 3166 2e31  7 : 0000:00:1f.1
00000d0: 0a20 2030 3137 302d 3031 3737 203a 206c  .  0170-0177 : l
00000e0: 6962 6174 610a 3031 6630 2d30 3166 3720  ibata.01f0-01f7 
00000f0: 3a20 3030 3030 3a30 303a 3166 2e31 0a20  : 0000:00:1f.1. 
0000100: 2030 3166 302d 3031 6637 203a 206c 6962   01f0-01f7 : lib
0000110: 6174 610a 3033 3736 2d30 3337 3620 3a20  ata.0376-0376 : 
0000120: 3030 3030 3a30 303a 3166 2e31 0a20 2030  0000:00:1f.1.  0
0000130: 3337 362d 3033 3736 203a 206c 6962 6174  376-0376 : libat
0000140: 610a 3033 6330 2d30 3364 6620 3a20 7667  a.03c0-03df : vg
0000150: 612b 0a30 3366 362d 3033 6636 203a 2030  a+.03f6-03f6 : 0
0000160: 3030 303a 3030 3a31 662e 310a 2020 3033  000:00:1f.1.  03
0000170: 6636 2d30 3366 3620 3a20 6c69 6261 7461  f6-03f6 : libata
0000180: 0a30 3830 302d 3038 3066 203a 2070 6e70  .0800-080f : pnp
0000190: 2030 303a 3035 0a30 6366 382d 3063 6666   00:05.0cf8-0cff
00001a0: 203a 2050 4349 2063 6f6e 6631 0a31 3030   : PCI conf1.100
00001b0: 302d 3130 3766 203a 2030 3030 303a 3030  0-107f : 0000:00
00001c0: 3a31 662e 300a 2020 3130 3030 2d31 3037  :1f.0.  1000-107
00001d0: 6620 3a20 706e 7020 3030 3a30 350a 2020  f : pnp 00:05.  
00001e0: 2020 3130 3030 2d31 3030 3320 3a20 4143    1000-1003 : AC
00001f0: 5049 2050 4d31 615f 4556 545f 424c 4b0a  PI PM1a_EVT_BLK.
0000200: 2020 2020 3130 3034 2d31 3030 3520 3a20      1004-1005 : 
0000210: 4143 5049 2050 4d31 615f 434e 545f 424c  ACPI PM1a_CNT_BL
0000220: 4b0a 2020 2020 3130 3038 2d31 3030 6220  K.    1008-100b 
0000230: 3a20 4143 5049 2050 4d5f 544d 520a 2020  : ACPI PM_TMR.  
0000240: 2020 3130 3130 2d31 3031 3520 3a20 4143    1010-1015 : AC
0000250: 5049 2043 5055 2074 6872 6f74 746c 650a  PI CPU throttle.
0000260: 2020 2020 3130 3230 2d31 3032 3020 3a20      1020-1020 : 
0000270: 4143 5049 2050 4d32 5f43 4e54 5f42 4c4b  ACPI PM2_CNT_BLK
0000280: 0a20 2020 2031 3032 382d 3130 3266 203a  .    1028-102f :
0000290: 2041 4350 4920 4750 4530 5f42 4c4b 0a20   ACPI GPE0_BLK. 
00002a0: 2020 2031 3036 302d 3130 3766 203a 2069     1060-107f : i
00002b0: 5443 4f5f 7764 740a 3131 3830 2d31 3162  TCO_wdt.1180-11b
00002c0: 6620 3a20 3030 3030 3a30 303a 3166 2e30  f : 0000:00:1f.0
00002d0: 0a20 2031 3138 302d 3131 6266 203a 2070  .  1180-11bf : p
00002e0: 6e70 2030 303a 3035 0a31 3430 302d 3134  np 00:05.1400-14
00002f0: 6666 203a 2050 4349 2043 6172 6442 7573  ff : PCI CardBus
0000300: 2023 3035 0a31 3634 302d 3136 3466 203a   #05.1640-164f :
0000310: 2070 6e70 2030 303a 3035 0a31 3830 302d   pnp 00:05.1800-
0000320: 3138 3166 203a 2030 3030 303a 3030 3a31  181f : 0000:00:1
0000330: 642e 300a 2020 3138 3030 2d31 3831 6620  d.0.  1800-181f 
0000340: 3a20 7568 6369 5f68 6364 0a31 3832 302d  : uhci_hcd.1820-
0000350: 3138 3366 203a 2030 3030 303a 3030 3a31  183f : 0000:00:1
0000360: 642e 310a 2020 3138 3230 2d31 3833 6620  d.1.  1820-183f 
0000370: 3a20 7568 6369 5f68 6364 0a31 3834 302d  : uhci_hcd.1840-
0000380: 3138 3566 203a 2030 3030 303a 3030 3a31  185f : 0000:00:1
0000390: 642e 320a 2020 3138 3430 2d31 3835 6620  d.2.  1840-185f 
00003a0: 3a20 7568 6369 5f68 6364 0a31 3836 302d  : uhci_hcd.1860-
00003b0: 3138 3766 203a 2030 3030 303a 3030 3a31  187f : 0000:00:1
00003c0: 642e 330a 2020 3138 3630 2d31 3837 6620  d.3.  1860-187f 
00003d0: 3a20 7568 6369 5f68 6364 0a31 3838 302d  : uhci_hcd.1880-
00003e0: 3138 3866 203a 2030 3030 303a 3030 3a31  188f : 0000:00:1
00003f0: 662e 310a 2020 3138 3830 2d31 3838 6620  f.1.  1880-188f 
0000400: 3a20 6c69 6261 7461 0a31 3861 382d 3138  : libata.18a8-18
0000410: 6162 203a 2030 3030 303a 3030 3a31 662e  ab : 0000:00:1f.
0000420: 320a 3138 6163 2d31 3861 6620 3a20 3030  2.18ac-18af : 00
0000430: 3030 3a30 303a 3166 2e32 0a31 3862 302d  00:00:1f.2.18b0-
0000440: 3138 6266 203a 2030 3030 303a 3030 3a31  18bf : 0000:00:1
0000450: 662e 320a 3138 6330 2d31 3863 3720 3a20  f.2.18c0-18c7 : 
0000460: 3030 3030 3a30 303a 3166 2e32 0a31 3863  0000:00:1f.2.18c
0000470: 382d 3138 6366 203a 2030 3030 303a 3030  8-18cf : 0000:00
0000480: 3a31 662e 320a 3138 6530 2d31 3866 6620  :1f.2.18e0-18ff 
0000490: 3a20 3030 3030 3a30 303a 3166 2e33 0a31  : 0000:00:1f.3.1
00004a0: 6330 302d 3163 6666 203a 2050 4349 2043  c00-1cff : PCI C
00004b0: 6172 6442 7573 2023 3035 0a32 3030 302d  ardBus #05.2000-
00004c0: 3266 6666 203a 2050 4349 2042 7573 2023  2fff : PCI Bus #
00004d0: 3031 0a20 2032 3030 302d 3230 6666 203a  01.  2000-20ff :
00004e0: 2030 3030 303a 3031 3a30 302e 300a 3330   0000:01:00.0.30
00004f0: 3030 2d33 6666 6620 3a20 5043 4920 4275  00-3fff : PCI Bu
0000500: 7320 2330 320a 2020 3330 3030 2d33 3031  s #02.  3000-301
0000510: 6620 3a20 3030 3030 3a30 323a 3030 2e30  f : 0000:02:00.0
0000520: 0a20 2020 2033 3030 302d 3330 3166 203a  .    3000-301f :
0000530: 2065 3130 3030 0a34 3030 302d 3466 6666   e1000.4000-4fff
0000540: 203a 2050 4349 2042 7573 2023 3033 0a66   : PCI Bus #03.f
0000550: 6530 302d 6665 3030 203a 2070 6e70 2030  e00-fe00 : pnp 0
0000560: 303a 3035 0a                             0:05.
```

The /sys/devices/pnp0/* all give no output

---

### Post by Favux on 2009-02-10
Alright.  It would be sweet if we knew the equivalent Stylistic to the finepoint your Gateway tablet has.  I'll study the output.  Meantime if you could disable setserial and retry the dmesg command, that would be good.  Let's see if it returns something different.

If inspiration strikes, speak up!

Edit:  It should be "jon@jon-laptop:~$ /proc/ioports" not "jon@jon-laptop:~$ xxd /proc/ioports"

---

### Post by jonthemiller on 2009-02-10
I'll do that as soon as I get off work later today.
I have gone through the man pages for the fpit deb install, and while they are slightly updated from the file you attached, their directions aren't any clearer or different.

---

### Post by Favux on 2009-02-10
Hi again jonthemiller,

The reason the dmseg is important is it should be giving the exact entry to put in your serial.conf file.  So if, with setserial disabled (uninstalled?),:
```
dmesg | grep ttyS
```
isn't giving the output try:
```
sudo dmesg |grep ttyS
```
It should be giving output something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
Which you would then add to your serial.conf file:
```
/dev/ttyS0 uart 16550A port 0x3f8 irq 4 baud_base 34800
```
And of course change ttyS3 in xorg.conf to ttyS0.

---

### Post by jonthemiller on 2009-02-10
After sudo apt-get remove setserial and a restart for good measure:
```
jon@jon-laptop:~$ dmesg | grep ttyS
jon@jon-laptop:~$ sudo dmesg | grep ttyS
jon@jon-laptop:~$ 
```
Neither gave any output.  This is where I have gotten stuck before, and I can't seem to find out how to find the setserial for the pen.

---

### Post by Favux on 2009-02-10
Hi jonthemiller,

We are so close to getting this!

Did you remember to in "/etc/serial.conf" remove the line "setserial /dev/ttyS3 autoconfig"? And then restart.

Dmesg should query the kernel buffer.  Serial info should be in the kernel buffer.  What else could interfere?  I guess you could also try removing the finepoint driver if the above doesn't work.

Otherwise it's suggesting what?  That your Hardy kernel (2.6.24-?) isn't detecting your serial devices?  That seems far-fetched.  You said the stylus etc. still works in Windows, right?

I've got a few configure lines for other M 285-E's from the forum and web.  Since they're all different you might have to try each one.  If you can't get yours.  They all seem to be on S0 though.

---

### Post by jonthemiller on 2009-02-10
I went back now and retried the "xxd /dev/ttyS0" after removing setserial and it works now. So, the pen is on ttyS0 right? I'm going to change the xorg.conf and restart to see if that helps.

Okay, the pen tracks and clicks (right clicks as well!) but the tracking is off.  I'm assuming some parameter in xorg.conf is off and will require some tweaking by me.  Thank you so much for helping me, you've been great!

---

### Post by Favux on 2009-02-10
Outstanding!

Correct, stylus is on S0.

You may be right and it is xorg.conf calibration.  I think I have some alternate xorg.conf calibrations from the same sources I got the "/etc/serial.conf" lines like "/dev/ttyS0 etc.".  Let me know if you want them.

Or it could be you need the correct "/dev/ttyS0 etc." line in your "/etc/serial.conf".  So don't give up on the dmesg stuff.

---

### Post by jonthemiller on 2009-02-10
As of right now "/etc/serial.conf" is a blank file.  The relevant contents of "/etc/X11/xorg.conf" follow:
```
Section "InputDevice"
	Identifier	"mouse0"
	Driver		"fpit"
	Option		"Device"	"/dev/ttyS0"
	# These may need tweaking.
	Option		"BaudRate"	"19200"
	Option		"MaximumXPosition"	"6250"
	Option		"MaximumYPosition"	"4950"
	Option		"MinimumXPosition"	"130"
	Option		"MinimumYPosition"	"0"
	Option		"InvertY"
	# For a passive pen, e.g. Stylistic 3400
        #Option		"Passive"
	# To make the touchscreen respond automatically to
	# resolution changes and screen rotation:
	Option		"TrackRandR"
EndSection
```
I was thinking of tweaking the Position variables to something more along the lines of described in here:
[http://ubuntuforums.org/showthread.php?t=429701](http://ubuntuforums.org/showthread.php?t=429701)  (post #6)

EDIT:  The X and Y position options set it perfectly.  I have perfect tracking now and the clicking is dead on.  It seems the side button is being interpreted as a  middle mouse button though.


That thread has, until now, been the most complete guide on solving this problem.  But, seeing as its almost 2 years old and written for Feisty it hasn't turned out as well as your help has been.

---

### Post by Favux on 2009-02-11
Hey jonthemiller,

Really good work!  Here is another old HOW TO:

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/howto-get-your-gateway-or-finepoint-pen-working-497879/]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/howto-get-your-gateway-or-finepoint-pen-working-497879/")

Just for completeness sake.

Is it possible that the new finepoint driver has obviated the need for the "/etc/serial.conf" line?  That seems to be what's happening.  And pretty cool too!

I think I read somewhere that just like in Wacom the finepoint generates a .xinitrc too.  If so it'll be a hidden file in your /home/username directory.  We could use that to change the side-switch to a right click.  If not we just need to figure out what the script files name and location is.  I'll look back at the readme.  Give me a few minutes and I'll get a version 2 of the xorg.conf and attach it.

Edit:  The coordinate positions seem the same.  Didn't you say you change them?

---

### Post by jonthemiller on 2009-02-11
Yeah, I just didn't reflect the changes in the post when I edited it.  Here they are:
```
Section "InputDevice"
	Identifier	"mouse0"
	Driver		"fpit"
	Option		"Device"	"/dev/ttyS0"
	# These may need tweaking.
	Option		"BaudRate"	"19200"
	Option		"MaximumXPosition"	"12550"
	Option		"MaximumYPosition"	"7650"
	Option		"MinimumXPosition"	"400"
	Option		"MinimumYPosition"	"400"
	Option		"InvertY"
	# For a passive pen, e.g. Stylistic 3400
#	Option		"Passive"
	# To make the touchscreen respond automatically to
	# resolution changes and screen rotation:
	Option		"TrackRandR"
EndSection
```

Also, I just looked through my home directory and didn't see a ".xinitrc" folder in there. A filesystem search didn't turn it either.  Is there an easy way to see what files are created/modified by a package during install?

---

### Post by Favux on 2009-02-11
> Is there an easy way to see what files are created/modified by a package during install? 
There may be but I don't know it.  I just finished the xorg.conf so I'll hit the script issue next.

As always back up your xorg.conf before trying the new one.  And look it over.  Mainly I just put in your new coordinates and tidied up.  Also added some Xorg header stuff that was missing.  Main change is to try to get a more descriptive Identifier than mouse0.  We know some folks used Tablet.  So I thought "Finepoint Tablet" would be good and descriptive.  If X and the driver permit it, of course.

Edit:  There is a way to see the files.  Use Synaptic Package Manager and search for the Package you used.  Then click on it and go to Packages and select Properties then click on the Installed Files tab.

---

### Post by Favux on 2009-02-11
Hi jonthemiller,

Okay, what I was remembering was this from the readme:
> Problem 1:  Side switch being reported as wild button numbers
	   (like 249 instead of 3): 

Solution:  Add the following to your xinitrc: 

	xsetpointer TOUCHSCREEN
	xmodmap -e 'pointer = 1 2 3'

This should be re-stating the defaults, but Aron Hsiao agrees that it appears
to be an XFree86 4.x bug. 
Now xinitrc is at "/etc/X11/xinit".  In my Wacom setup xinitrc has stuff in it but it is all commented out.  In fact if it tries to invoke Xsession it needs to be commented out like so:
```
# invoke global X session script
#. /etc/X11/Xsession
```
But I don't know if the applies to Finepoint.  You could follow the chain of scripts to see if there are any Finepoint entries.  But the only syntax I know to manipulate the buttons is Wacom, which almost certainly doesn't apply to Finepoint.  So I'll keep reading.  It would have been nice if this stuff was in the README.  You said you had a slightly newer readme.  Does it talk about any of this?

Edit:  Look at what I found:

[https://help.ubuntu.com/community/FujitsuStylus]("https://help.ubuntu.com/community/FujitsuStylus")

While the title seems "misleading", after you think about it, it really isn't.  But no wonder we missed it!

---

### Post by jonthemiller on 2009-02-11
> **Favux said:**
> Does it talk about any of this?

Edit:  Look at what I found:

[https://help.ubuntu.com/community/FujitsuStylus]("https://help.ubuntu.com/community/FujitsuStylus")

While the title seems "misleading", after you think about it, it really isn't.  But no wonder we missed it!

I wonder why that page never showed up in any google searches I did.  Strange.  Anyway, the updated file was from the deb FPIT, and only told what needed to be changed in xorg and such.  I will follow the instructions on the help.ubuntu.com site above.  If anything, the title should at least be updated to allow finding it easier.

Edit: Did the changes that page recommended, and all is well (except having to execute a script to have tablet left click but oh well)  Thanks again for all your patient help, I don't know what I would have done without you.

---

### Post by Favux on 2009-02-11
Hi jonthemiller,

Before you do that can you tell me where you are with functionality?

And I did find one listing:
```
Option     "Buttons"     "2"
```
in the xorg.conf of a bug poster who was correcting the fpit driver code.  So I think he probably had a clue.  We could also try changing 2 to 3 if 2 doesn't work. 	I'd try it just below the ttyS0 line and above the tweak comment.  There just doesn't seem to be any instructions on Options and Option format like the Wacom HOW TO has.

Edit:  I'm not sure I'd want to try the button fix the wiki poster suggested.  It seems pretty awkward.

---

### Post by jonthemiller on 2009-02-11
> **Favux said:**
> Hi jonthemiller,

Before you do that can you tell me where you are with functionality?

And I did find one listing:
```
Option     "Buttons"     "2"
```
in the xorg.conf of a bug poster who was correcting the fpit driver code.  So I think he probably had a clue.  We could also try changing 2 to 3 if 2 doesn't work. 	I'd try it just below the ttyS0 line and above the tweak comment.  There just doesn't seem to be any instructions on Options and Option format like the Wacom HOW TO has.

Edit:  I'm not sure I'd want to try the button fix the wiki poster suggested.  It seems pretty awkward.

Yeah, it would be.  The main click works, but the side button is interpreted as button 3.  If I hit the side button and move the pen it activates the cube rotation in compiz (like the middle mouse button does on my bluetooth mouse).  Hmmm, so variable in xorg I'm missing? Or can I make a script that will set button 3 to button 2?  I know some bash scripting but not enough to do this, I'm a ruby programmer in real life.

---

### Post by Favux on 2009-02-12
> I'm a ruby programmer in real life. 
Cool.

I did find one man page, which seems very dated.

[http://linux.die.net/man/4/fpit]("http://linux.die.net/man/4/fpit")

I thought I bookmarked that bug, but I guess not.

So where are we?  Did you test xorg 2?  Did "Finepoint Tablet" work?  Did you try inserting the button option?

Have I mentioned my rotation HOW TO?

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

My stylus has one button or side-switch.  To make it a right click in the stylus section of my xorg.conf:
```
	Option		"Button2"	"3"    # make side-switch a R button
```
to make it a middle button:
```
	Option		"Button2"	"2"    # make side-switch a middle button
```
I'm hoping something analogous will work for Finepoint.  Everything I read had complaints about the buttons.

---

### Post by jonthemiller on 2009-02-12
> **Favux said:**
> So where are we?  Did you test xorg 2?  Did "Finepoint Tablet" work?  Did you try inserting the button option?

Have I mentioned my rotation HOW TO?

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

My stylus has one button or side-switch.  To make it a right click in the stylus section of my xorg.conf:
```
	Option		"Button2"	"3"    # make side-switch a R button
```
to make it a middle button:
```
	Option		"Button2"	"2"    # make side-switch a middle button
```
I'm hoping something analogous will work for Finepoint.  Everything I read had complaints about the buttons.

xorg.conf 2 works for me.  I have it set with the buttons option and with Button2 now working as a Right Click.  I'll take a look at the screen rotation later tonight and see if I can figure that out.  Its a shame that no one has figured out how to utilize the buttons beneath the screen on the M-285/295, from what I've read they are a windows only type of deal.

---

### Post by Favux on 2009-02-12
Hi jonthemiller,

Wow!  Outstanding work.  I'd love to see your current xorg.conf.  I don't know why, but I'm getting a charge out of "Finepoint Tablet" working.

Yeah, on the TX's we only have two out of our four bezel buttons working.  No one's figure out what, if any, signal the non-functioning ones are putting out.

---

### Post by jonthemiller on 2009-02-13
> **Favux said:**
> Hi jonthemiller,

Wow!  Outstanding work.  I'd love to see your current xorg.conf.  I don't know why, but I'm getting a charge out of "Finepoint Tablet" working.

Yeah, on the TX's we only have two out of our four bezel buttons working.  No one's figure out what, if any, signal the non-functioning ones are putting out.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"		"xorg"
	Option		"XkbModel"		"pc105"
	Option		"XkbLayout"		"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "InputDevice"
	Identifier	"Finepoint Tablet"
	Driver		"fpit"
	Option		"Device"		"/dev/ttyS0"
	Option		"Buttons"		"2"
	Option		"Button2"		"3"
	Option		"BaudRate"		"19200"
	Option		"MaximumXPosition"	"12550"
	Option		"MaximumYPosition"	"7650"
	Option		"MinimumXPosition"	"400"
	Option		"MinimumYPosition"	"400"
	Option		"InvertY"
	Option		"TrackRandR"
	Option		"Passive"		"false"
	Option		"SendCoreEvents"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"Finepoint Tablet"
	Inputdevice	"mouse0"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

There's the entire thing, working for me on a M-285-E with Ubuntu 8.04 Hardy Heron with all latest updates to today.  FPIT is the 1:1.2.0-1 Debian install.  Setserial version is 2.17.  Hardware specs as follows:
[LIST]
[*]Intel 2.0 GHz Core 2 Duo
[*]2 GB RAM
[*]100 GB 7200 RPM SATA HDD
[*]ATI X1400 Mobility video chipset running the restricted ATI drivers
[/LIST]

Thanks again for all your help with this drawn out issue.

---

### Post by Favux on 2009-02-13
Hi jonthemiller,

You're welcome.  It has been fun tinkering with the M 285-E with you!  I appreciated you persevering through the process.  Thank you.

PS:  I think you may want to comment out or remove 
"Inputdevice	"mouse0"" from the ServerLayout since it's shouldn't be doing anything.

---

