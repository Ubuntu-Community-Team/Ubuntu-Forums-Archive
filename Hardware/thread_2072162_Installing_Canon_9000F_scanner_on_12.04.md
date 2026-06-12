---
title: "Installing Canon 9000F scanner on 12.04"
date: 2012-10-17
forum: Hardware
---

### Post by pcradwick on 2012-10-17
Having spent a few days struggling with this - pouring over the web as others have done, I thought I would put up my notes in case it might help others. I didn't get it entirely right, but using others experience (many thanks) it finally worked. Maybe someone can correct the mistakes i.e. un-installing existing (old) backends.


Check scanner is supported in [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)
It is in pixma backend.

Download sane 1.0.23 backend from [https://alioth.debian.org/frs/?group_id=30186](https://alioth.debian.org/frs/?group_id=30186)
Use instructions in README to combine files
Merge sane backend downloads:
$ cat sane-backends-1.0.23.tar.gz.[1-3] > sane-backends-1.0.23.tar.gz

Checksum:
$ md5sum -c sane-backends-1.0.23.tar.gz.md5
  sane-backends-1.0.23.tar.gz: OK

unzip/untar file

Following instructions in:		[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)
$ cd .../sane-backends-1.0.23
$ make clean
$ sudo apt-get install libusb-dev build-essential libsane-device
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

*** WARNING: SANE is already installed (version 1.0.23). The old
*** installation is at /usr/local while SANE will now be installed
*** at /usr. It is recommended to uninstall the old SANE version
*** before installing the new one to avoid problems.

[I was guessing here. I didn't really know how to uninstall 
the old version. However I believe in retrospect that if this 
is done correctly here the 'miracle' step at the end that got 
it all working by redirecting the link would probably be unecessary.]

Remove installed version
$ sudo make uninstall

Remove sane from /usr/local
$ ./configure --prefix=/usr/local
$ sudo make uninstall

Prepare for proper installation once again
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

*** Warning: An old version of SANE was detected but the sane-config program
*** couldn't be found. If you encounter any problems with SANE remove the old
*** SANE files and reinstall this version.

??? I obviously haven't done this right, but carried on...

Compile and install backend source code:
$ sudo make
$ sudo make install

Plug in scanner, turn on
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 004: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 002 Device 003: ID 12f7:2000 Memorex Products, Inc. 
Bus 002 Device 004: ID 1058:1023 Western Digital Technologies, Inc. 
Bus 002 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 007: ID 04a9:1908 Canon, Inc. 
Bus 001 Device 006: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 008: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 008: ID 04f9:0027 Brother Industries, Ltd HL-2030 Laser Printer

Scanner detected

$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9, product=0x1908) at libusb:001:010
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

Found scanner but not identified comletely - no names
  
$ sudo sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x1908 [CanoScan]) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Names now found so permissions problem
First add user to scanner group
$ sudo adduser <username> scanner

Copy scanner rule(s) for udev to fix permissions
This file already has the entry (among others) for setting permissions for group 'scanner'
# Canon CanoScan 9000F
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1908", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"
$ cp .../sane-backends-1.0.23/tools/udev/libsane.rules /etc/udev/rules.d/libsane.rules

This solves permissions problem and sane-find-scanner now gives correct output without 'sudo'

$ scanimage -L
[pixma] udp_command: no data received (recv): Connection refused[pixma] udp_command: no data received (recv): 
Connection refused[pixma] udp_command: no data received (recv): 
Connection refused[pixma] Cannot read scanner make & model: H&#65533;&#65533;
device `v4l:/dev/video0' is a Noname Laptop_Integrated_Webcam_1.3M virtual device

Following: [http://lists.alioth.debian.org/pipermail/sane-devel/2012-May/029838.html](http://lists.alioth.debian.org/pipermail/sane-devel/2012-May/029838.html)

$ scanimage -V
scanimage (sane-backends) 1.0.23; backend version 1.0.22

Version mixup because of existing old version?

Check result of original installation:
$ ls -l /usr/lib/sane/libsane-pixma*
-rwxr-xr-x 1 root root    954 Oct 14 17:12 /usr/lib/sane/libsane-pixma.la
lrwxrwxrwx 1 root root     23 Oct 14 17:12 /usr/lib/sane/libsane-pixma.so -> libsane-pixma.so.1.0.23
lrwxrwxrwx 1 root root     23 Oct 14 17:12 /usr/lib/sane/libsane-pixma.so.1 -> libsane-pixma.so.1.0.23
-rwxr-xr-x 1 root root 508608 Oct 14 17:12 /usr/lib/sane/libsane-pixma.so.1.0.23

Check for earlier versions of libsane-pixma
$ ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-pixma*

-rw-r--r-- 1 root root 235006 Dec  5  2011 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.a
-rw-r--r-- 1 root root    979 Dec  5  2011 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.la
lrwxrwxrwx 1 root root     23 Dec  5  2011 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so -> libsane-pixma.so.1.0.22
lrwxrwxrwx 1 root root     23 Dec  5  2011 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so.1 -> libsane-pixma.so.1.0.22
-rw-r--r-- 1 root root 138064 Dec  5  2011 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so.1.0.22

Change link to point to newly installed libraries (1.0.23):
$ cd /usr/lib/x86_64-linux-gnu/sane
$ ln -i -s /usr/lib/sane/libsane-pixma.so.1.0.23 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so.1

Result:
$ ll libsane-pixma*
-rw-r--r-- 1 root root 235006 Dec  5  2011 libsane-pixma.a
-rw-r--r-- 1 root root    979 Dec  5  2011 libsane-pixma.la
lrwxrwxrwx 1 root root     23 Dec  5  2011 libsane-pixma.so -> libsane-pixma.so.1.0.22
lrwxrwxrwx 1 root root     37 Oct 17 16:56 libsane-pixma.so.1 -> /usr/lib/sane/libsane-pixma.so.1.0.23*
-rw-r--r-- 1 root root 138064 Dec  5  2011 libsane-pixma.so.1.0.22

Scanner is directly connected to usb port (not network) so
comment out line in /etc/sane.d/pixma.conf "bjnp://127.0.0.1"

$ scanimage -L
device `v4l:/dev/video0' is a Noname Laptop_Integrated_Webcam_1.3M virtual device
device `pixma:04A91908' is a CANON Canoscan 9000F multi-function peripheral

xsane finds scanner (and the Webcam) and it all works!

---

### Post by pdc on 2012-10-17
well done; 

you have learnt a lot about the scanner commands: very thorough description and very useful to many others I am sure;

you infer it was the new version of sane caused the hiccups..I would wonder about that ..but still..

...............help us understand why you installed sane 1.0.23 (as opposed to just using what was already installed?)

---

### Post by aikishugyo on 2012-10-17
Hi,
If you would do just a normal install instead of configuring to overwrite your existing installation (never a good idea) you would have had no troubles, with the new sane in /usr/local.

---

### Post by danieleday on 2013-01-18
Genius! After several tries I found your thread and followed your instructions for changing the link, and magic! It finally works.
Thanks a lot. Now I can switch off my Windows VM.

p.s. I had permissions problems as well, so for other novices like me, in the ./configure command at the start use "prefix=/usr**/local"** instead of "prefix=/usr"  and the same for changing the link at the end:

ln -i -s /usr**/local**/lib/sane/libsane-pixma.so.1.0.23 /usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so.1

---

### Post by rb1234 on 2013-01-19
For the CS9000F it is save to install the daily git snapshot of Sane 1.0.24 from here: [http://www.sane-project.org/cvs.html](http://www.sane-project.org/cvs.html).

With the source files comes a good installation desription "Step by step install on Linux 2.6.* and 3.*" in README.linux.

---

### Post by johnG43 on 2013-07-20
This was a great write up.  I have a Canon MG3200 that I was trying setup so I followed these instructions.  Problem is, SANE does not list this printer.

I did eventually get it to work, so if you have one of these, read on.  First get the model number from lsusb (mine was 1762, but check lsusb anyway).  Next you need to add that model number to the libsane.rules file.  Finally, edit the backend/pixma_mp150.c file where the MG3100 series is defined (two spots). Add these two lines in the appropriate spots:

 #define MG3200_PID 0x1762  
and
DEVICE ("Canon PIXMA MG3200", "MG3200", MG3200_PID, 1200, 0, 0, 638, 877, PIXMA_CAP_CIS),

Make sure the PID define matches what you got from lsusb.  Compile and install along with the rules change for udev.

My MG3200 is working now both with usb and wireless.

---

### Post by philromford-q on 2014-03-13
I have spent days trying to get ny canoscan 9000F to connect. I think it  is almost there,but not quite. I'll explain, this is what I have done:-

I  firstly got the 1.0.24 backend, compiled and installed that, having the  same problem in attempting to uninstall 1.0.22. I still don't know how  to do that. This first attempt failed; not being seen by: $ sudo scanimage -L.

I then downloaded the GIT 1.0.25 files and tried that, still not working. I then tried 1.0.23, still not working.

I have now gone back to 1.0.24 My current set up is this:-

$ lsusb
Bus 001 Device 012: ID 04a9:1908 Canon, Inc. 

$ sudo lsusb
Bus 001 Device 012: ID 04a9:1908 Canon, Inc. 

$ sane-find-scanner
found USB scanner (sudo vendor=0x04a9, product=0x1908) at libusb:001:012

$ sudo sane-find-scanner
found USB scanner (vendor=0x04a9 [Canon], product=0x1908 [CanoScan]) at libusb:001:012

$ scanimage -L
device `pixma:04A91908' is a CANON Canoscan 9000F multi-function peripheral

$ sudo scanimage -L
device `pixma:04A91908' is a CANON Canoscan 9000F multi-function peripheral

$ scanimage -T
scanimage: open of device pixma:04A91908 failed: Access to resource has been denied

$ sudo scanimage -T
scanimage: open of device pixma:04A91908 failed: Device busy

$ scanimage -V
scanimage (sane-backends) 1.0.24; backend version 1.0.22

$ sudo scanimage -V
scanimage (sane-backends) 1.0.24; backend version 1.0.22

I  have ensured that I am in the 'scanner group', and have checked  permissions for the libsane-pixma* files in /usr/lib/sane and in  /usr/lib/i386-linux-gnu/sane; making all part of the scanner group.

I have also worked through the steps in this link: [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

To include:-

sudo gedit /lib/udev/rules.d/40-libsane.rules   adding the 9000F

To make sure that the newest version of sane (in /usr/local/lib/sane) is used 
gksu gedit /etc/ld.so.confTo use the old version it should read 
include /etc/ld.so.conf.d/*.conf include /usr/libTo use the new version, change it to  
include /etc/ld.so.conf.d/*.conf include /usr/local/libThen run 
sudo ldconfig

Having  done all this it still does not connect. Clearly, I am missing  something somewhere but I don't know what. I'm puzzled by the return  from:-

scanimage -V

As this still seems to say that the backend is 1.0.22 surely that should not be so.

Could you possibly help please?

Thank you

---

### Post by philromford-q on 2014-03-13
[ATTACH=CONFIG]251110[/ATTACH]

This is what I get if I try to start Xsane.

---

### Post by philromford-q on 2014-03-13
I forgot to say that I renamed libsane-pixma-1.0.22 so that it is effectively archived; only 1.0.24 files are in the libraries.

---

### Post by pdc on 2014-03-13
It is all a bit strange;

if one goes to SANE: scanning for linux

[http://www.sane-project.org/](http://www.sane-project.org/)

and one looks in the Canon section

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

...specifically for the 9000F, they say it is [COLOR="#008000"]Complete[/COLOR] (fully supported);

similarly we have a Canon 650U; it also is [COLOR="#008000"]Complete[/COLOR]; and it just ...works..........

I wonder if you subscribe to the SANE mailing list; [http://www.sane-project.org/mailing-lists.html](http://www.sane-project.org/mailing-lists.html) to see if the experts there can help you 

There is a guy called aikishugyo who posts on these forums: does canon development in the SANE project I think; you could try a private message to him 

[http://ubuntuforums.org/member.php?u=167122](http://ubuntuforums.org/member.php?u=167122)

---

### Post by philromford-q on 2014-03-14
Yes, it is all a bit strange - to me as a beginner especially.

No, I currently don't subscribe to the SANE project, however, I will now!

Thank you for the suggestion.

---

### Post by philromford-q on 2014-03-14
Yes, it is all a bit strange - to me as a beginner especially.

No, I currently don't subscribe to the SANE project, however, I will now!

Thank you for the suggestion.

---

### Post by rb1234 on 2014-03-14
If you want to install SANE from git, please follow the installation description in README.linux or here: [http://www.sane-project.org/README.linux](http://www.sane-project.org/README.linux).

If you simply want to use SANE from the latest git sources, you can use this ppa: 'sudo add-apt-repository ppa:rolfbensch/sane-git'.

---

### Post by aikishugyo on 2014-03-14
> **rb1234 said:**
> If you want to install SANE from git, please follow the installation description in README.linux or here: [http://www.sane-project.org/README.linux](http://www.sane-project.org/README.linux).

If you simply want to use SANE from the latest git sources, you can use this ppa: 'sudo add-apt-repository ppa:rolfbensch/sane-git'.

Yes, that is the correct way, no confusion.
I developed the initial driver, but Rolf is now the official maintainer of the pixma backend, and much more capable than I will ever be.
Regards,
Gernot Hassenpflug

---

### Post by philromford-q on 2014-03-15
After a great deal of tweaking config files, I finally have it working! However, what I did to make it work doesn't quite match the instructions in the SANE readme - interesting.

The results in Treminal are now:-

> $ sudo ldconfig -v | grep libsane
/sbin/ldconfig.real: Can't stat /lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Can't stat /usr/lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Path `/lib/i386-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/i386-linux-gnu' given more than once
    libsane.so.1 -> libsane.so.1.0.22
    libsane.so.1 -> libsane.so.1.0.25
phil@phil-Desktop:~$ scanimage -V
scanimage (sane-backends) 1.0.25git; backend version 1.0.22



Not what I expected, but it works. I have yet to work through XSANE to check for full functionality, but that's front end stuff.

I'm currently making a 4800 dpi scan: I'm surprised to see how slow it is though, compared to when running a similar scan under Windows 7 with the Canon software.

---

### Post by philromford-q on 2014-03-15
It has been quite a struggle to get the scanner working. It could be that I made some wrong steps initially that took all this time to correct. If you look at my last post for the terminal outputs, you can see what appears to be wrong, in that the order of backends is wrong, and 'scanimage -V' returns 1.0.22 as the backend! Very odd.

Can this be explained I wonder.

Thank you everyone for your suggestions. Maybe I can help someone else one day.

---

### Post by pdc on 2014-03-15
you got it working: well done: enjoy

---

### Post by aikishugyo on 2014-03-15
Check your path.
The git 1.0.25 should be first because it is in /usr/local/lib which in path should come before /usr/lib.
It is hard to tell what might be wrong with only the current output (everything from console should be saved to log file by redirection or by a script to run the commands).
But if you ever messed up the standard system by over-writing something, it makes things difficult later. Hence, the instructions and the default into /usr/local as expected for "local" installations of software.

Here a standard type of wrapper for scripted commands, just call them step1, step2, etc., if you run more commands later.
> #!/bin/sh
(
date
<commands here>
date
) 2>&1 | tee -a step1.log

---

### Post by philromford-q on 2014-03-15
> **aikishugyo said:**
> Check your path.
The git 1.0.25 should be first because it is in /usr/local/lib which in path should come before /usr/lib.
It is hard to tell what might be wrong with only the current output (everything from console should be saved to log file by redirection or by a script to run the commands).
But if you ever messed up the standard system by over-writing something, it makes things difficult later. Hence, the instructions and the default into /usr/local as expected for "local" installations of software.

Here a standard type of wrapper for scripted commands, just call them step1, step2, etc., if you run more commands later.

1.0.25 actually installed in      /usr/lib/sane
1.0.22 is in                            /usr/lib/i386-linux-gnu/sane

I haven't moved any files, so this is how 1.0.22 was filed during my Ubuntu install. Libsane placed 1.0.25 without my intervention - all rather odd is it not?

Thank you for the commands, I will look at this later.

Right now I just glad to have it working.

---

