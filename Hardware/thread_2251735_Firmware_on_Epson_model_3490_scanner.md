---
title: "Firmware on Epson model 3490 scanner"
date: 2014-11-06
forum: Hardware
---

### Post by joverstreet1 on 2014-11-06
I have an Epson model 3490 scanner on which the firmware does not seem to permanently reside on the hardware of the scanner but the firmware has to be **reloaded **(from file on hard drive of computer) to the scanner each and every time the power (AC) is turned off to the scanner.  

Various forum instructions mention inserting line for loading binary file Esfw52.bin into configuration file to get the firmware loaded as part of getting this scanner to function.

I had never heard of this situation regarding firmware before.  On all of the other devices I have ever dealt with hard drives, motherboards, video cards, etc., etc. they retain the firmware even if the AC is cut off to them.

Is it the norm that scanner hardware devices have to have the firmware reloaded to them after each and every power down or is this due to the fairly old age of this Epson 3490 scanner ?

Thanks.

---

### Post by Pilot6 on 2014-11-06
There is a native linux driver. It can be found here.

[http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

There is no need to use Windows .bin file.

---

### Post by joverstreet1 on 2014-11-06
> **Pilot6 said:**
> There is a native linux driver. It can be found here.

[http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

There is no need to use Windows .bin file.

These do NOT work, I have already tried.

Thanks.

---

### Post by MIJ-VI on 2014-11-07
Years ago I successfully used **alien** (it's in the repos) to convert *LaCie LightScribe Labeler 1.0 Linux.rpm* into *4l_1.0-1_i386.deb*

[ubuntu] Epson 3490 scanner
[http://ubuntuforums.org/showthread.php?t=2249897](http://ubuntuforums.org/showthread.php?t=2249897)

Epson Perfection 3490 Photo, Drivers & Downloads - Technical Support - Epson Canada, Limited.
[http://www.epson.ca/cgi-bin/ceStore/support/supDetail.jsp?oid=58609&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX](http://www.epson.ca/cgi-bin/ceStore/support/supDetail.jsp?oid=58609&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX)

EPSON Download Center
[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Ubuntu, how to convert .rpm to .deb at DuckDuckGo
[https://duckduckgo.com/?q=Ubuntu%2C+how+to+convert+.rpm+to+.deb](https://duckduckgo.com/?q=Ubuntu%2C+how+to+convert+.rpm+to+.deb)

---

### Post by joverstreet1 on 2014-11-07
> **MIJ-VI said:**
> Years ago I successfully used **alien** (it's in the repos) to convert *LaCie LightScribe Labeler 1.0 Linux.rpm* into *4l_1.0-1_i386.deb*

[ubuntu] Epson 3490 scanner
[http://ubuntuforums.org/showthread.php?t=2249897](http://ubuntuforums.org/showthread.php?t=2249897)

Epson Perfection 3490 Photo, Drivers & Downloads - Technical Support - Epson Canada, Limited.
[http://www.epson.ca/cgi-bin/ceStore/support/supDetail.jsp?oid=58609&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX](http://www.epson.ca/cgi-bin/ceStore/support/supDetail.jsp?oid=58609&BV_UseBVCookie=yes&infoType=Downloads&platform=OSF_O_LINUX)

EPSON Download Center
[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Ubuntu, how to convert .rpm to .deb at DuckDuckGo
[https://duckduckgo.com/?q=Ubuntu%2C+how+to+convert+.rpm+to+.deb](https://duckduckgo.com/?q=Ubuntu%2C+how+to+convert+.rpm+to+.deb)

Like I said, I tried this but it lets you to use the scanner as long as you don't turn it off.  Turn it off and you have to go thru this entire process all over again.  Not acceptable !!!

Thanks.

---

### Post by coldraven on 2014-11-07
I know it's not the same model but I have been using the method here to use my 1670 on every version of Ubuntu without any problems:
It acts perfectly normal, I just plug the scanner in and start scanning. 
I guess that there is not not much electronics in the scanner, all the work is done by the software.
[http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html)

---

### Post by MIJ-VI on 2014-11-07
> **joverstreet1 said:**
> Like I said, I tried this but it lets you to use the scanner as long as you don't turn it off.  Turn it off and you have to go thru this entire process all over again.  Not acceptable !!!

Thanks.

Sorry joverstreet1. It was past my bed time.

Having no experience troubleshooting scanners (my old CanoScan 650 'just works'), here's the two options I could scare up before I have to run out the door:

From my Ubuntu 14.04.1-based linuxmint-17-mate-64bit-v2 install: /etc/sane.d/epson.conf

> # USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0

--

If time costs more than a bit of try-before-you-buy money:

I used to use VueScan with a PPC Mac. It was excellent.

Epson Perfection 3490 Scanner Driver and Software | VueScan
[http://www.hamrick.com/vuescan/epson_perfection_3490.html](http://www.hamrick.com/vuescan/epson_perfection_3490.html)

This may come in handy:

Perfection 3490 PHOTO - Product Information Guide - pr349ppg.pdf
[https://files.support.epson.com/pdf/pr349p/pr349ppg.pdf](https://files.support.epson.com/pdf/pr349p/pr349ppg.pdf)

---

### Post by joverstreet1 on 2014-11-07
> **MIJ-VI said:**
> Sorry joverstreet1. It was past my bed time.

Having no experience troubleshooting scanners (my old CanoScan 650 'just works'), here's the two options I could scare up before I have to run out the door:

From my Ubuntu 14.04.1-based linuxmint-17-mate-64bit-v2 install: /etc/sane.d/epson.conf



--

If time costs more than a bit of try-before-you-buy money:

I used to use VueScan with a PPC Mac. It was excellent.

Epson Perfection 3490 Scanner Driver and Software | VueScan
[http://www.hamrick.com/vuescan/epson_perfection_3490.html](http://www.hamrick.com/vuescan/epson_perfection_3490.html)

This may come in handy:

Perfection 3490 PHOTO - Product Information Guide - pr349ppg.pdf
[https://files.support.epson.com/pdf/pr349p/pr349ppg.pdf](https://files.support.epson.com/pdf/pr349p/pr349ppg.pdf)

Thanks, [**[COLOR=#000000]MIJ-VI[/COLOR]**]("http://ubuntuforums.org/member.php?u=955375"):

Not going to pay for software to get scanner to work on Linux when it works perfectly fine on Windows (which I don't want to use - even though the scanner works on MS).

Also, have no idea as to what the actual parameters are suppoed to be for that Linux configuration file even though I have asked several places (includining here) and even posted the results of my lsusb output and tried every combination that I could come up with - none of which resulted in proper function of the scanner. 

Thanks.

---

### Post by coldraven on 2014-11-08
> Is it the norm that scanner hardware devices have to have the firmware  reloaded to them after each and every power down or is this due to the  fairly old age of this Epson 3490 scanner ?

I don't think you have grasped what is happening. The firmware is not being sent to the scanner the whole process is being emulated in software.
Inside your scanner are just  two motors and some buttons, there is no CPU or memory chip for firmware to reside.
Exactly the same process happens whether you scan from Windows or Linux.

As I already posted above, **I only have to do the configuration once**. After that the scanner behaves normally each time it is used. It is the first thing I do when I install a new version of Ubuntu and has worked every time. The 1670 gives excellent results.
I cannot tell if my model is older or newer than yours, any idea?

You can copy esfw52.bin from your Windows installation and it should work for you as well.

---

### Post by joverstreet1 on 2014-11-11
> **coldraven said:**
> I don't think you have grasped what is happening. The firmware is not being sent to the scanner the whole process is being emulated in software.
Inside your scanner are just  two motors and some buttons, there is no CPU or memory chip for firmware to reside.
Exactly the same process happens whether you scan from Windows or Linux.

As I already posted above, **I only have to do the configuration once**. After that the scanner behaves normally each time it is used. It is the first thing I do when I install a new version of Ubuntu and has worked every time. The 1670 gives excellent results.
I cannot tell if my model is older or newer than yours, any idea?

You can copy esfw52.bin from your Windows installation and it should work for you as well.

Coldraven:

Your scanner must be constructed differently from this model 3490 because if I install the software from within an old copy of windows 2000 which I have on my machine (which apparently includes that FIRMWARE which is loaded to the scanner's memory) and then if I boot back to my Linux OS, the scanner works just fine all day long using the Linux Simplescan application as long as I don't turn the power off to the scanner.  I can restart or shutdown my computer under Linux and as long as I DON'T turn the power off to the scanner it will always function perfectly, i.e. scan, however, the moment that I turn the power off to the scanner and back on, it will no longer scan, i.e. because turning off the power to the scanner, empties the memory that the firmware is residing in.  But I don't want to have to boot into windows every time I want to do some scanning !!!

Also, I have found that trying to use the Esfw52.bin file as part of the scanner configuration on my Linux OS is a big NO, NO, because it corrupts files and folders on my Linux OS.

Thanks.

---

### Post by coldraven on 2014-11-15
> Also, I have found that trying to use the Esfw52.bin file as part of the  scanner configuration on my Linux OS is a big NO, NO, because it  corrupts files and folders on my Linux OS.


How does it corrupt your files?

If as you say the firmware is being sent to a chip in the scanner and works OK until powered down then it would make no difference if it was sent via Windows or Linux. 
I have had absolutely no problems and I've been using that config on each version of Ubuntu since 2005. Maybe your scanner has some special functions that do not play well with Linux. 
Now I think of it I do not use the buttons on my scanner, I just scan from my PC. I believe it has a button that scans to email but I have never used it. It could I suppose try to open a non-existent Windows email client and try to write to disk using a Windows path variable.
Maybe that's what is causing your problem. I'm sorry that I cannot be more helpful.

---

