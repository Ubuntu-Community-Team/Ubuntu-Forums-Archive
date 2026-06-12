---
title: "Ricoh webcam still not working even with appropiate drivers!!!"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by HalphaZ on 2007-11-19
Hi...
I've a big problem. big big problem.
First of all, presentations:

uname -a
```
stefano@stefano-laptop:~$ uname -a
Linux stefano-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

lsusb
```
stefano@stefano-laptop:~$ lsusb
Bus 001 Device 004: ID 0518:0005 EzKEY Corp. 
Bus 001 Device 005: ID 062a:0201 Creative Labs 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05ca:1810 Ricoh Co., Ltd   <-- bad bad bad device...
Bus 002 Device 001: ID 0000:0000  
stefano@stefano-laptop:~$ 
```

from [http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.22-14-generic/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.22-14-generic/) I downloaded  this file: ricoh-webcam-r5u870-2.6.22-14-generic_0.10.0-4_i386.deb and I saved it into the desktop. I double-clicked it and a window said that all dependencies were ok. So I installed this .deb and I restarted.

Camorama says me "unable to capture image" and closes. Before of this the blue led near the camera lights up for a while.

aMSN isn't able of doing something... just an error window...

Kopete makes his windows appear, but is unusable and uses 100% of my CPU, so I've to kill him (before installing this driver, kopete worked properly).

gqcam
```
stefano@stefano-laptop:~$ gqcam -v /dev/video0 
Segmentation fault (core dumped)
```

my dmesg during this tries:
dmesg    -- >  post attachment

my dmesg | grep -i r5:
```
stefano@stefano-laptop:~$ dmesg | grep -i r5
[   18.056000] usbcam: registering driver r5u870 0.10.0
[   18.056000] r5u870-0: Detected HP Pavilion Webcam
[   18.224000] usbcore: registered new interface driver r5u870
[   79.216000] r5u870-0: set_format: fmtidx:1 frameidx:1 640x480 ival:500000
[  199.100000] r5u870-0: set_format: fmtidx:1 frameidx:4 320x240 ival:500000
[  321.552000] r5u870-0: set_format: fmtidx:1 frameidx:1 640x480 ival:500000
[ 2261.548000] r5u870-0: could not set altsetting: -110
[ 2262.948000] r5u870-0: warning: short frame (exp:614400 got:477131)
[ 2351.584000] r5u870-0: uvc_req 01/0200/0200 failed: -110
[ 2762.676000] r5u870-0: uvc_req 01/0200/0200 failed: -110
stefano@stefano-laptop:~$ 
```


I need help... please...

(I'm not english... sorry for my language's mistakes...)

---

### Post by HalphaZ on 2007-11-20
Please, if someone has the same problem, post here...
I feel so alone...

---

### Post by N8K99 on 2007-11-25
you are not alone. I had the webcam working until I went to get a video editor package and now no longer have the webcam

---

### Post by davejrice on 2007-11-28
Is there any progress on this yet - I'm having, what seems to be, the exact same problem as HalphaZ.  The symptoms are the same - blue LED lights up, but various programs throw their teddies out the cots with various errors.

I'm on a HP DV9233eu (AMD x2, 1024mb, nv7600 - 05ca:1810 Ricoh Co., Ltd)

cheers

---

### Post by davejrice on 2007-11-28
However!!!!  I just found the Skype 2.0beta

[http://www.skype.com/intl/en/download/skype/linux/beta/choose/](http://www.skype.com/intl/en/download/skype/linux/beta/choose/)

and the camera works!  At least in the preferences dialogue test area! I saw myself - scarey!!!

don't know why it doesn't work anywhere else tho.

cheers

---

### Post by buchalkalan on 2008-01-11
check the permissions of /dev/video and /dev/video0, 

do a chmod 777 /dev/video*

and after that check your webcam, it worked for me in this way, though I am using fedora 8.

---

### Post by ekaprits on 2008-02-10
I have a similar problem. My webcam is not working with Skype 2.0 beta or any other webcam-capturing application. It used to work with the driver ricoh-webcam-r5u870 version 0.10.0-4, but after some problems in Skype, I installed ricoh-webcam-r5u870-2.6.22-14-generic version 0.10.0-4 and now the webcam no longer works with Skype or anything else.

However, when I do a 
> cat /dev/video0
I can see the webcam working and producing some output.

I have already tried doing a chmod 777 /dev/video* but nothing changed.

btw, my uname -a is:
> 
Linux manos-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

I would like to know if there is something I can do to uninstall all existing modules regarding the webcam, so I can start fresh (or any other solution to this problem).

Any help is appreciated!

---

### Post by majoorpa on 2008-02-11
I also have the same problem. As informed by someone earlier I also found that With the latest beta of skype the webcam is working.

With others it is not.


I am using dv9000 series HP laptop
Ubuntu 7.10 kernel 2.6.22-14-generic
usb id: 05ca:1810


Anybody got it working?

majoorpa

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

