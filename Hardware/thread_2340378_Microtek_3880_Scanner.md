---
title: "Microtek 3880 Scanner"
date: 2016-10-18
forum: Hardware
---

### Post by Kevin McCready on 2016-10-18
I can't get scanner working and suspect the drivers in sane xsane may not work. Or I don't know how to set up permissions.

I've plugged this in via usb.
```

lsusb
Bus 002 Device 004: ID 05da:3021 Microtek International, Inc. 1200dpi Scanner
```

I found this website
[http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/)
but the advice might be outdated and I haven't tried to compile or modify source code (I don't have those skills).

When I try to run vuescan from the command line, it says 'command not found'.

When I run vuescan by clicking on the file it doesn't find the scanner. The vuescan.ini file reads:
[VueScan]
[Input]
Source=0
[Prefs]
WindowXOffset=96
WindowYOffset=53
WindowXSize=1728
WindowYSize=946

I don't know if I can alter this .ini file to find the scanner.

When I run
```
sane-find-scanner

```
it lists lots of USB's then says for each 'Access denied (insufficient permissions)'

```
sudo scanimage -L

```
doesn't help.

I forget what I did to get this output:
```

found USB scanner (vendor=0x05da [Prolific Technology Inc.], product=0x3021 [USB Scanner               ]) at libusb:002:004
found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

Any help would be greatly appreciated.

---

### Post by Kevin McCready on 2016-10-19
I think it might be that I need to adjust the permissions of vuescan. I tried to do this in sudoers but it didn't work. Is there another way to set the permissions of a program. I installed vuescan by clicking on a tar.gz file.

---

### Post by kurt18947 on 2016-10-19
Did you run Vuescan from a user account? I've used Vuescan and didn't install anything, just extracted the archive into a folder then made sure the Vuescan binary was marked as executable and checked that two other files - I don't recall their names - were in the same folder. Double click the Vuescan binary and it launched.

---

### Post by Bucky Ball on 2016-10-20
Install Simple Scan from the repos and try that. Install from Software Centre, Synaptics or a terminal.

---

### Post by Kevin McCready on 2016-10-20
Thanks guys.
simple-scan didn't find the scanner.

[ATTACH=CONFIG]271696[/ATTACH]

I've attached a copy of the vuescan directory. The vuescan file is executable. When I click on it I get 3 options Execute, Execute in Terminal, Cancel. When I click on either of the first two I get an error message that the scanner couldn't be found. Item 6 of the error message (the first 5 items are not the problem) says in part "try running VueScan as root to see if it's a libusb device protection problem."

---

### Post by kurt18947 on 2016-10-21
> **Kevin McCready said:**
> Thanks guys.
simple-scan didn't find the scanner.

[ATTACH=CONFIG]271696[/ATTACH]

I've attached a copy of the vuescan directory. The vuescan file is executable. When I click on it I get 3 options Execute, Execute in Terminal, Cancel. When I click on either of the first two I get an error message that the scanner couldn't be found. Item 6 of the error message (the first 5 items are not the problem) says in part "try running VueScan as root to see if it's a libusb device protection problem."

Well, here's the problem with Viewscan:

[https://www.hamrick.com/vuescan/microtek_scanmaker_3880.html](https://www.hamrick.com/vuescan/microtek_scanmaker_3880.html)


                                               [TABLE="class: table table-striped table-bordered"]
[TR]
[TD="align: right"]Flatbed Scanning:[/TD]
[TD="align: right"]Yes[/TD]
[/TR]
               [TR]
[TD="align: right"]Film Scanning:[/TD]
[TD="align: right"]No[/TD]
[/TR]
               [TR]
[TD="align: right"]Document Feeder:[/TD]
[TD="align: right"]No[/TD]
[/TR]
               [TR]
[TD="align: right"]Windows:[/TD]
[TD="align: right"]Yes[/TD]
[/TR]
               [TR]
[TD="align: right"]Mac:[/TD]
[TD="align: right"]No[/TD]
[/TR]
               [TR]
[TD="align: right"][B]Linux:
[/B][/TD]
[TD="align: right"]**No**
[/TD]
[/TR]
               [TR]
[TD="align: right"]USB:[/TD]
[TD="align: right"]Yes[/TD]
[/TR]
               [TR]
[TD="align: right"]SCSI:[/TD]
[TD="align: right"]No[/TD]
[/TR]
               [TR]
[TD="align: right"]Firewire:[/TD]
[TD="align: right"]No[/TD]
[/TR]
               [TR]
[TD="align: right"]Network:[/TD]
[TD="align: right"]No
[/TD]
[/TR]
               [TR]
[TD="align: right"]USB Vendor ID:[/TD]
[TD="align: right"]05da
[/TD]
[/TR]
               [TR]
[TD="align: right"]USB Product ID:[/TD]
[TD="align: right"]3021
[/TD]
[/TR]
               [TR]
[TD="align: right"]Optical DPI:[/TD]
[TD="align: right"]1200
[/TD]
[/TR]
[/TABLE]


I guess your only shot with that scanner would be with SANE. I have no experience there so no help I'm afraid.

---

### Post by Kevin McCready on 2016-10-22
SANE also says it doesn't support this scanner. BUT someone has written a SANE driver and patch which  might work.
[http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/)
That website says ... It may work with other ScanMaker 3800 or 4800 series scanners, but their USB IDs will need to be patched into the source code (sane_get_devices).

Source files are provided below.  You first need to install  [sane-backends-1.0.15]("http://www.sane-project.org/source.html") and then install the following patch and tar.gz file over them:

    patch -p1 < [sm3840_patch**2**]("http://www.ziplabel.com/sm3840/sm3840_patch2")
   tar zvxf [sm3840_source**5**.tar.gz]("http://www.ziplabel.com/sm3840/sm3840_source5.tar.gz")
 
Once the source files are installed execute

    ./configure && make clean && make && make install

----
So I extracted 
sane-backends-1.0.15-1.0.16.diff.gz
from
[https://alioth.debian.org/frs/?group_id=30186](https://alioth.debian.org/frs/?group_id=30186)

I created a file called 'sm3840_patch2'
=
~/Downloads $ sudo subl sm3840_patch2

I tried to installed the patch =
patch -p1 < sm3840_patch2
this gave error and asked what file it should patch. I told it=
sane-backends-1.0.15-1.0.16.diff.gz

But it said "No such file or directory"

So I'm stuck. Please help again.

---

### Post by Kevin McCready on 2016-10-23
Ooops I was working with the wrong file. So I managed to compile the right one and got this error:

make[1]: *** No rule to make target 'sm3840.c', needed by 'sm3840.lo'.  Stop.
make[1]: Leaving directory '/home/k/Downloads/sane-backends-1.0.15/backend'
Makefile:116: recipe for target 'all-recursive' failed
make: *** [all-recursive] Error 1

The website said "USB IDs will need to be patched into the source code (sane_get_devices)." But I have no idea what file the source code is in (is it the patch)? Do I put the "patch into the source code" before I apply the patch and compile?

---

