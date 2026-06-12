---
title: "HP ScanJet 3200C not working"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by amrtuti on 2007-05-08
Friends,
I'm quite new to Linux. I've been using Windows 98 as my primary OS and is planning a complete switchover to Linux. My installation of Ubuntu (and SUSE) are to my full satisfaction except the fact that my scanner won't work. It is a HP ScanJet 3200C, connected via parallel port along with HP LaserJet 1100A printer. Unlike the printer, the scanner wasn't auto-detected.
When starting a scan application, the error message was 'no devices available'. In addition,  my installation of the latest SANE backend (downloaded) too proved unsuccessful. While invoking the './configure' command, it creates an error message, which I give below.
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "xsane"
| #define VERSION "0.994"
| #define XSANE_PACKAGE_VERSION "xsane-0.994"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1853: error: C compiler cannot create executables
See `config.log' for more details.
I'll be grateful for your help in this regard.
Allwyn

---

### Post by glavspirt on 2007-05-17
Try to build sane-backends from cvs:
```
sudo cvs -z3 -d:pserver:anonymous@cvs.alioth.debian.org:/cvsroot/sane co sane-backends
```
Remove from your system libsane package before. 
Then in /usr/local/etc/sane.d/ comment all backends in dll.conf except umax_pp and edit umax_pp.conf.

I am now trying to get it work too, but I just started.

---

### Post by glavspirt on 2007-05-18
I have got it working!!!
It is much simplier than I though, works almost out of the box.

1. Just comment all backends except umax_pp
```
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
#net
#abaton
#agfafocus
#apple
#avision
#artec
#artec_eplus48u
#as6e
#bh
#canon
#canon630u
##canon_pp
#coolscan
#coolscan2
##dc25
##dc210
##dc240
#dell1600n_net
#dmc
#epson
#fujitsu
##gphoto2
#genesys
#gt68xx
#hp
#hpsj5s
#hp3500
#hp4200
#hp5400
#ibm
#leo
#lexmark
#ma1509
#matsushita
#microtek
#microtek2
#mustek
##mustek_pp
#mustek_usb
#mustek_usb2
#nec
#niash
#pie
#pixma
#plustek
##plustek_pp
##pnm
#qcam
#ricoh
#s9036
#sceptre
#sharp
#sm3600
#sm3840
#snapscan
#sp15c
##st400
##stv680
#tamarack
#teco1
#teco2
#teco3
##test
#u12
#umax
umax_pp
#umax1220u
#v4l

```

2. Edit umax_pp.conf
```
# For documentation see sane-umax_pp(5)

# GLOBAL #

# size (in bytes) of scan buffer (default: 2 megabyte)
option buffer 2097152


# DEVICES #

# specify the port your scanner is connected to. 
#
# the value 'auto' will make the backend find the correct value
# by itself, it will scan  ppdev, ppi device, then hardware address
# 'safe-auto' will do the same but won't do direct hardware access
# on linux systems, you may provide the device name of the ppdev character 
# device : /dev/parport0, /dev/parport1, ......
#
# on *BSD, you may provide the device name of the ppi device: /dev/ppi0,
# /dev/ppi1, ...
#
# Possible hardware addresses are 0x378 (lp0)
# 0x278 (lp2) and 0x3c8 (lp1)
#

port auto

# the following options are local to this scanner
# gain for red channel, if not given, will be automatically computed
# must be between 0 and 15
#option red-gain 8

# gain for green channel, if not given, will be automatically computed
# must be between 0 and 15
#option green-gain 4

# gain for blue channel, if not given, will be automatically computed
# must be between 0 and 15
#option blue-gain 8

# offset for red channel, if not given, will default to 0
# must be between 0 and 15
#option red-offset 2

# offset for green channel, if not given, will default to 0
# must be between 0 and 15
#option green-offset 1

# offset for blue channel, if not given, will default to 0
# must be between 0 and 15
#option blue-offset 1


#
#
# model number
#
# valid values are 610, 1220, 1600 and 2000
#
# by default, no model, we rely on autodetection
# in case you have black or 'inverted' scans, 
# you may override detection by providing the
# model number
#option astra 1220

```

3. Make sure you have EPP or ECP+EPP modes enabled in your BIOS

---

### Post by Mike_Longbow on 2007-07-19
I just want to thank glavspirt. This helped me a lot with my scanner. Yeah! \\:D/

---

### Post by uninewbee on 2007-09-10
> **glavspirt said:**
> Try to build sane-backends from cvs:
```
sudo cvs -z3 -d:pserver:anonymous@cvs.alioth.debian.org:/cvsroot/sane co sane-backends
```
Remove from your system libsane package before. 
Then in /usr/local/etc/sane.d/ comment all backends in dll.conf except umax_pp and edit umax_pp.conf.

I am now trying to get it work too, but I just started.


How do you "Remove from your system libsane package before"?
and do you mean before you do above or after?

---

### Post by glavspirt on 2007-10-18
The second posting was the answer to uninewbee (sudo apt-get remove libsane). It is absolutely unnecessary, if you want to get the scanner working. Third posting is complete enough.

---

### Post by zuup on 2007-10-29
Thank You! glavspirt :lolflag:

I made it working...

But... quality of images is poor. Colors needs a lot of tweaking and worst there are stripes :mad:

With Win Xp the same scanner (3200C) works just fine.

Can anyone help? Probably editing xsane settings is enough?

---

### Post by glavspirt on 2007-10-30
Greetings! Unfortunately, I am far away from that scanner, but I have ssh access to the machine with that. Playing with xsane properties is enough, but I don´t remember which options I had alternated. Maybe that helps ~/.sane/xsane/UMAX:Astra1220P.drc
```

"XSANE_DEVICE_RC"
"UMAX:Astra 1220P"
"xsane-version"
"0.991"
"mode"
"Grayscale"
"resolution"
19660800
"preview"
0
"preview-in-gray"
0
"tl-x"
2827
"tl-y"
3414
"br-x"
4752
"br-y"
5886
"lamp-control"
1
"custom-gamma"
0
"manual-channel-gain"
0
"manual-offset"
0
"xsane-main-window-x-position"
1
"xsane-main-window-y-position"
50
"xsane-main-window-width"
314
"xsane-main-window-height"
483
"xsane-project-window-x-position"
280
"xsane-project-window-y-position"
425
"xsane-standard-options-window-x-position"
1
"xsane-standard-options-window-y-position"
400
"xsane-advanced-options-window-x-position"
280
"xsane-advanced-options-window-y-position"
420
"xsane-histogram-window-x-position"
280
"xsane-histogram-window-y-position"
50
"xsane-gamma-window-x-position"
280
"xsane-gamma-window-y-position"
420
"xsane-batch-window-x-position"
480
"xsane-batch-window-y-position"
420
"xsane-preview-window-x-position"
0
"xsane-preview-window-y-position"
0
"xsane-preview-window-width"
803
"xsane-preview-window-height"
660
"xsane-gamma"
49082
"xsane-gamma-red"
65536
"xsane-gamma-green"
65536
"xsane-gamma-blue"
65536
"xsane-brightness"
4929699
"xsane-brightness-red"
-2261861
"xsane-brightness-green"
2493847
"xsane-brightness-blue"
1449911
"xsane-contrast"
352052
"xsane-contrast-red"
-1681897
"xsane-contrast-green"
-1681897
"xsane-contrast-blue"
4465727
"xsane-lineart-mode"
0
"xsane-threshold"
3276800
"xsane-threshold-min"
0
"xsane-threshold-max"
6553600
"xsane-threshold-multiplier"
65536
"xsane-threshold-offset"
0
"xsane-grayscale-scanmode"
""
"xsane-enhancement-rgb-default"
0
"xsane-negative"
0
"xsane-show-preview"
0


```

"From the box" I had red coloured scanned images with horizontal stripes. But now all is right, except sometimes vertical yellow stripes, which was in Windows too. Yellow colour occures from the backlight lamp, it needs to be changed :KS. What is really cool in xsane that I can choose quality of image (change dpi in main window).

---

### Post by zuup on 2007-10-30
Okay, thanks

From the Box results were exactly same for me (red colored scanned images with horizontal stripes).

I tried your settings and result was green/blue colored images. And when I increased red stripes came back :confused:

So maybe I have messed up some other settings...

---

### Post by glavspirt on 2007-10-30
Curiously :confused: maybe users have changed smth there. When I will there (I do not know when exactly) I can look. I think that your settings are OK.
It is definitely colour settings. Try to play with them in xsane.  
When I reach the scanner I will report, check out thread later.

---

### Post by zuup on 2007-10-31
Ok

I think I can handle colours, stripes might be a problem...

---

### Post by glavspirt on 2008-04-18
Unfortunately, my scanner had died :(

---

