---
title: "canon pixma MP270"
date: 2009-08-19
forum: Hardware
---

### Post by Chrus on 2009-08-19
So I got a new printer today, but stupidly forgot to check if it would work in linux. And guess what, it doesnt.

Ive tried drivers for a few different canon models, and the generic drivers, but cant get anything out of it.

Is there anything else I can try? Any way to use the windows drivers? Or should I just return it and get a printer thats going to work?

Cheers

---

### Post by Excedio on 2009-08-19
I have a Canon MP460 but have it setup as if i'm using a Canon MP150. Don't know itf that will work for you....but it did for me.

---

### Post by Chrus on 2009-08-19
I tried the 150, 160, 170 and 180... no luck with any of them :(

---

### Post by Chrus on 2009-08-19
Given up... taking it back for a refund.

---

### Post by coldReactive on 2009-08-20
> **Chrus said:**
> Given up... taking it back for a refund.

Next time you might want to print out a printer and scanner list.

openprinting.org

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

### Post by Chrus on 2009-08-20
> **coldReactive said:**
> Next time you might want to print out a printer and scanner list.

openprinting.org

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Brilliant! Thanks mate. Will make sure to check that before I get another printer.

---

### Post by UKer on 2009-11-16
Just in case anyone else is searching, this printer works flawlessly with Turboprint

:popcorn::guitar:

---

### Post by Jan S on 2009-11-18
You can find the Canon drivers from Canon Australia site. Should work with cups... Well at least the printing works. I can't get the scanner to work.

---

### Post by Jan S on 2009-11-20
Scanner drivers come with a scanning software scangearmp. I got everything working.

---

### Post by heepie on 2009-11-24
Thank you very much... had the same problem....

---

### Post by nikink on 2009-11-26
> **Jan S said:**
> You can find the Canon drivers from Canon Australia site. Should work with cups... Well at least the printing works. I can't get the scanner to work.

Today I compiled Sane 1.0.21 git snapshot 20091125, backend and frontends and xscanimage works 

(take care compiling frontends from git snapshot 20091125 requires to uncomment an ifdef in sane.h so that these are defined:
```

#define SANE_STATUS_WARMING_UP 12 /* lamp not ready, please retry */
#define SANE_STATUS_HW_LOCKED  13 /* scanner mechanism locked for transport */

```

 and modify configure script and substitute check for sane version >= 1.1.0 into >=1.0.21)

---

### Post by nikink on 2009-11-26
> **nikink said:**
> Today I compiled Sane 1.0.21 git snapshot 20091125, backend and frontends and xscanimage works 

(take care compiling frontends from git snapshot 20091125 requires to uncomment an ifdef in sane.h so that these are defined:
```

#define SANE_STATUS_WARMING_UP 12 /* lamp not ready, please retry */
#define SANE_STATUS_HW_LOCKED  13 /* scanner mechanism locked for transport */

```

 and modify configure script and substitute check for sane version >= 1.1.0 into >=1.0.21)

To use the scanner as non root user add a file sane-pixma270.rules in /etc/udev/rules.d and write in it this row:
```

SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="173b", MODE="0664", GROUP="scanner"

```
then create the group scanner and add you to the group scanner. After that reboot.
If you don't want to reboot, make sure you are in the group scanner (use groups command), then you have to restart udev and turn off and on again the printer, if you don't turn off and on the printer the settings in the file sane-pixma270.rules will not apply.

I also find canon drivers in the japan site. See this page:
[http://cweb.canon.jp/drv-upd/bj/bjlinux320.html](http://cweb.canon.jp/drv-upd/bj/bjlinux320.html)

and find PIXUS MP270, there are deb and rpm packages. I'm trying the deb. It's only for printer functions.

---

### Post by nikink on 2009-11-27
> **nikink said:**
> I also find canon drivers in the japan site. See this page:
[http://cweb.canon.jp/drv-upd/bj/bjlinux320.html](http://cweb.canon.jp/drv-upd/bj/bjlinux320.html)

and find PIXUS MP270, there are deb and rpm packages. I'm trying the deb.

I successfull installed debian version of japan printer driver, version 3.2.
I downloaded the deb package from [http://cweb.canon.jp/drv-upd/bj/bjlinux320.html](http://cweb.canon.jp/drv-upd/bj/bjlinux320.html) for the pixus MP270.

After extracting the contents of the archive i run the install.sh script as root (sudo).
If required install libusb-dev package.
When the install.sh tryes to detect the printer it doesn't find it, so i pressed Q to quit.
After that i rebooted the system with the printer turned on and the printer installed itself automatically.

If it doesn't work try to create a new printer and when it asks for model, choose the use PPD file option and browse to the ppd installed by the canon packages, it's in /usr/share/ppd/canonmp270.ppd.

---

### Post by nikink on 2009-11-27
> **nikink said:**
> I successfull installed debian version of japan printer driver, version 3.2.
I downloaded the deb package from [http://cweb.canon.jp/drv-upd/bj/bjlinux320.html](http://cweb.canon.jp/drv-upd/bj/bjlinux320.html) for the pixus MP270.
.....



I found link also for the scangear application, in the japanese site:

[http://cweb.canon.jp/drv-upd/bj/mpsglinux140.html](http://cweb.canon.jp/drv-upd/bj/mpsglinux140.html)

but i not yet tested it.

---

### Post by nikink on 2009-11-27
> **nikink said:**
> I found link also for the scangear application, in the japanese site:

[http://cweb.canon.jp/drv-upd/bj/mpsglinux140.html](http://cweb.canon.jp/drv-upd/bj/mpsglinux140.html)

but i not yet tested it.

Scangearmp installed and tested, no problems, just a sudo install.sh. Then run scangearmp. PERFECT.

---

### Post by jonas1980 on 2010-01-29
Perfect! I installed the Japanese drivers, rebooted the computer, and it's working great. 

I had to create a launcher for ScanGear, it is located in /usr/bin/scangearmp

Thanks guys!

---

### Post by Ça&#287;r&#305; on 2010-05-08
Thnx a lot, I also had the same problem : )

Cheers

---

### Post by last1home on 2010-12-15
If it doesn't work try to create a new printer and when it asks for  model, choose the use PPD file option and browse to the ppd installed by  the canon packages, it's in /usr/share/ppd/canonmp270.ppd


Nice ...tnx

last1home

---

### Post by Maddog Battie on 2011-01-10
The drivers are also on the European website:
[http://software.canon-europe.com/products/0010753.asp](http://software.canon-europe.com/products/0010753.asp)

The all graphical install process:

[LIST]
[*]Download the printer driver (debian printer driver 3.2) and open in archive manager.

[*]Double click on cnijfilter-mp270series-3.20-1-i386-deb.tar.gz to open that.

[*]Double click on the packages directory.

[*]Double click on the cnijfilter-common_3.20-1_i386.deb file.

[*]Hit install then quit out.

[*]Double click on the cnijfilter-mp270series_3.20-1_i386.deb file.

[*]Hit install then quit out.

[*]Go System->Administration->Printing.

[*]Click on Add. Wait a while... (10 secs)

[*]Hopefully something like USB Printer #1 with status readback for Canon IJ will appear. Select it and then hit forward.

[*]Adjust names if required. Hit apply. You should now be up and running for printing.
[/LIST]

---

### Post by Maddog Battie on 2011-01-10
For the scanner the process is similar:

[LIST]
[*]Download the ScanGear for Linux 1.4 and open in archive manager

[*]Double click on scangearmp-mp270series-1.40-1-i386-deb.tar.gz

[*]Double click on scangearmp-mp270series-1.40-1-i386-deb

[*]Double click on packages.

[*]Double click on scangearmp-common_1.40-1_i386.deb

[*]Hit install then quit out.

[*]Double click on sacngearmp-mp270series_1.40-1_i386.deb

[*]Hit install then quit out.
[/LIST]

That did it for me. I could then operate the scanner from Gimp.

---

### Post by mediax on 2011-04-10
Apologies for reviving an old thread, but how do I get this install to work on an AMD64 machine?  I've followed the above instructions and get a "Wrong architecture 'i386'" error.

Thanks

---

### Post by zlobster on 2011-08-07
> **mediax said:**
> Apologies for reviving an old thread, but how do I get this install to work on an AMD64 machine?  I've followed the above instructions and get a "Wrong architecture 'i386'" error.

Thanks

Hola!

I got the same problem here.

```
Linux Alpha 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

And when I try to do the install the mentioned way...

```
chosenone@Alpha:~/Downloads/MP270_debian_driver_pack/cnijfilter-mp270series-3.20-1-i386-deb$ sudo ./install.sh 
[sudo] password for chosenone: 
==================================================

Canon Inkjet Printer Driver Ver.3.20-1 for Linux
Copyright CANON INC. 2001-2009
All Rights Reserved.

==================================================
Error! Cannot specify package management system.
```

'Cannot specify package management system'? WTF?

Looked into install.sh but since I'm a n00b I couldn't find the root cause for this #$%^. Any suggestions? Besides the ones telling me I need to chill a bit. :D

BTW, I'm running Natty on this box.

---

### Post by J-E-N-O-V-A on 2011-10-08
This thread was extremely useful.

---

