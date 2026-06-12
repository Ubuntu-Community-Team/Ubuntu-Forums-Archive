---
title: "Can I use Fujitsu Snapscan S300 Scanner with Ubuntu?"
date: 2009-07-19
forum: Hardware
---

### Post by markw10 on 2009-07-19
I am interested in buying a small portable scanner since I'll often use it on the go and the one I'm looking at is the Fujitsu Snapscan 300.  There is a M version, the 300M that's said to work with Macs.
My situation is I have a Mac at home and want to be able to use it with that so may have to get the 300M but also on the go I use a laptop that uses Ubuntu Linux.  
My question:  Will the 300, hopefully the Snapscan 300M work with Linux?  I want to make sure it will recognize the scanner.  Also, assuming it works what programs would I use to scan? I want to be able to scan into both jpgs and pdf's.  Thank you for your help.

---

### Post by mgmiller on 2009-08-09
I just went through this with a Fujitsu fi-6130.  It is not supported in 9.04, but is in 9.10.  I also paid the driver developer to add support for automatic page detection which it won't do by default in 9.10.

In fact. after a bit of back and forth, we (he, actually) got it working for me in 9.04 as well. 

Anyway, here is the list of supported fujitsu scanners in 9.04:
```
#fi-4x20C
usb 0x04c5 0x1041
usb 0x04c5 0x1042

#fi-5750C
usb 0x04c5 0x1095

#fi-5110xxx
usb 0x04c5 0x1096
usb 0x04c5 0x1097

#fi-5650C
usb 0x04c5 0x10ad

#fi-4x20C2
usb 0x04c5 0x10ae
usb 0x04c5 0x10af

#fi-5x20C
usb 0x04c5 0x10e0
usb 0x04c5 0x10e1

#fi-5530C
usb 0x04c5 0x10e2

#fi-5900C
usb 0x04c5 0x10e7

#fi-5110EOXM
usb 0x04c5 0x10f2

#scansnap S500
usb 0x04c5 0x10fe

#scansnap S500M
usb 0x04c5 0x1135

#scansnap S510
usb 0x04c5 0x1155

```And here is the longer list of supported Fujitsus' in 9.10:
```
#fi-4x20C
usb 0x04c5 0x1041
usb 0x04c5 0x1042

#fi-4530C
usb 0x04c5 0x1078

#fi-5750C
usb 0x04c5 0x1095

#fi-5110eox/2
usb 0x04c5 0x1096

#fi-5110C
usb 0x04c5 0x1097

#fi-5650C
usb 0x04c5 0x10ad

#fi-4x20C2
usb 0x04c5 0x10ae
usb 0x04c5 0x10af

#fi-4340C
usb 0x04c5 0x10cf

#fi-5x20C
usb 0x04c5 0x10e0
usb 0x04c5 0x10e1

#fi-5530C
usb 0x04c5 0x10e2

#fi-5110eox3
usb 0x04c5 0x10e6

#fi-5900C
usb 0x04c5 0x10e7

#fi-5110EOXM
usb 0x04c5 0x10f2

#ScanSnap S500
usb 0x04c5 0x10fe

#ScanSnap S500M
usb 0x04c5 0x1135

#fi-5530C2
usb 0x04c5 0x114a

#fi-6140
usb 0x04c5 0x114d

#fi-6240
usb 0x04c5 0x114e

#fi-6130
usb 0x04c5 0x114f

#fi-6230
usb 0x04c5 0x1150

#ScanSnap S510
usb 0x04c5 0x1155

#ScanSnap S510M
usb 0x04c5 0x116f

#fi-6770
usb 0x04c5 0x1174

#fi-6770A
usb 0x04c5 0x1175

#fi-6670
usb 0x04c5 0x1176

#fi-6670A
usb 0x04c5 0x1177

#fi-6750S
usb 0x04c5 0x1178

#S1500
usb 0x04c5 0x11a2

```The application I use the most is xsane which is in your Applications > Graphics menu.  Unless it sees a recognized scanner, it won't start up.

It can do scanning to jpg, png, pdf, multpage pdf, batch scanning and a whole pile of other things.

If you like, you can contact the guy who wrote the fujitsu driver and see how much he would want to write the backend for your S300.  Or you could buy a scanner that is or shortly will be supported.

His name is Allen and his email is kitno455 at gmail dot com.

---

### Post by IcarusR on 2009-08-10
As said above Xsane is used for scanning in Linux & should be installed by default in Ubuntu. 
Xsane is a front end to Sane that interfaces with individual backends (drivers) for the scanner. 
According to the 'supported devices' page on the Sane site
[http://www.sane-project.org/sane-mfgs.html#Z-FUJITSU]("http://www.sane-project.org/sane-mfgs.html#Z-FUJITSU") 
the Snapscan S300 should work. S300M however is untested.
Best to stick with the S300, or check the link for one that works better.

---

### Post by mgmiller on 2009-08-10
I stand corrected.  The s300 is supported in Ubuntu 9.04.  

Thanks to the link provided by the last poster, I see it doesn't use the fujitsu backend, rather it uses the epjitsu backend, hence my (incorrect) comment above that it was not supported.

Why does this sound like someting from Naruto?  :lolflag:


Plug it in, turn it on and fire up xsane and it should work with the caveats listed on the sane page:
"Duplex, 150/225/300/600 dpi, binary/gray/color, AC/USB power, buttons/sensors all supported. Scanner always scans in _triplex_ color, fast USB required. Calibration only fair at high resolution."

:popcorn:

---

### Post by sjpn on 2009-09-10
I just got my s300 b/c it was supported on sane. I am still not able to get it to scan though. I copied the windows driver (something like 300C0....nal) file like others said to the /etc/xsane.d/epjitsu directory (it was something like that) and it still doesn't recognize it. When I start xsane, it says it is having trouble accessing the built in webcam.... ??? Any ideas?

---

### Post by sjpn on 2009-09-10
sorry. it works now. I had to change a 300A... to a 300C... in the epjitsu config file. it works and i'm happy now :) 
scan quality is not as nice as windows for some reason, it seems more grainy and has more noise speckles. also it doesn't seem to create multipage pdf's. i tried gscan2pdf, but the duplex didn't seem to work right. but overall, i'm very pleased.

---

