---
title: "canon mf4100 series scanning"
date: 2008-08-03
forum: Hardware
---

### Post by quackeroni_pizza on 2008-08-03
I have the Canon multifunction printer-scanner-fax device MF4100 setup to print using the CUPS drivers.. I am looking for ways to enable scanning. I tried searching sane's supported devices but couldn't locate this device.

---

### Post by phidia on 2008-08-03
From a terminal what does > scanimage -L ouput?

The open printing site lists a MF4120 as working "partially". You may want to look at [their entry]("http://openprinting.org/show_printer.cgi?recnum=Canon-MF4120") on that printer-maybe something there will help.

---

### Post by quackeroni_pizza on 2008-08-06
Part of my problem is that my MF4100 is on a network... but I tried hooking it up directly and I got the following message from sane-find-scanners

> 
found USB scanner (vendor=0x04a9 [Canon Inc.], product=0x26a3 [MF4100]) at libusb:005:006


The output of scanimage -L is less encouraging..

> 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---

### Post by quackeroni_pizza on 2008-08-06
Ok after digging around for a while, I've managed to get my scanner to work when connected to USB.. Apparently someone has already written but not tested a sane backend for the MF4100 and other Canon devices..

Here's a summary of what I did-

I downloaded the latest sane-backend source from the sane-backend CVS of 2008-08-05... 
> [http://www.sane-project.org/cvs.html](http://www.sane-project.org/cvs.html)

I then compiled and installed the sane-backend following instructions from the README..

I added an entry for my device in 
> 
/etc/udev/rules.d/<some_prefix>libsane.rules

# Canon ImageClass MF4150
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="26a3", MODE="0664", GROUP="scanner", 



I added myself to group 'scanner' in /etc/group to get around any permission issues..

I then rebooted once to allow permission to take effect..
scanimage -L now works as follows

> 
device `pixma:04A926A3_SDF680281822B' is a CANON Canon imageCLASS MF4150 multi-function peripheral


xsane works fine...

---

### Post by jo_6466 on 2008-09-07
have you a cups for the MF4120?

---

### Post by quackeroni_pizza on 2008-09-16
I believe the sane backend works for all MF4100 series devices...
What is the output code from lsusb for your device?

My lsusb output includes this line...

[HTML]
Bus 005 Device 010: ID 04a9:26a3 Canon, Inc. MF4100 Series
[/HTML]

Is your code one of the following? [clipped from backend/pixma_imageclass.c]

[HTML]
#define MF4200_PID 0x26b5
/* the following are all untested */
#define MF5630_PID 0x264e
#define MF5650_PID 0x264f
#define MF8100_PID 0x2659
#define MF5730_PID 0x265d
#define MF5750_PID 0x265e
#define MF5770_PID 0x265f
#define MF3110_PID 0x2660
#define MF3200_PID 0x2684
#define MF6500_PID 0x2686
#define MF4100_PID 0x26a3
#define MF4600_PID 0x26b0
#define MF4010_PID 0x26b4
[/HTML]

---

### Post by quackeroni_pizza on 2009-04-19
I recently upgraded to Jaunty and can report that I still have to recompile sane-backends from the latest CVS source to get the scanner to work.. rather unfortunate..

All you have to do now is download the source, compile it and add appropriate permissions for the USB device/port and you should be good to go... 

Too bad, sane-backends hasn't been upgraded to reflect the pixma backend additions since last year...

---

### Post by quackeroni_pizza on 2009-09-19
Ok, the new UFR-II drivers 1.9 from the Canon Singapore website now let printing work on Jaunty.. Whoosh!

---

### Post by slickvguy on 2010-01-27
In case anyone stumbles across this thread, I found a post on a blog that finally solved the problem for me. I am very pleased. I have a canon MF4150 and recently upgraded to Jaunty.

[PIXMA Linux Blog - Give your scanner a new fresh SANE installation]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")

---

### Post by Andyhunter on 2011-02-11
Hello. And somebody could make it work the Scan button on the device. Ie when you press the button on the device is scanning. :confused:

---

