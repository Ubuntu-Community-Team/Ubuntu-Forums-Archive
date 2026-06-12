---
title: "HP PSC 2210 Not scanning"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by Avi on 2005-03-13
Hi,

I've spent a large chunk of my evening trying to get my HP PSC 2210 to scan - no success!

I've read tons of pages, hpoj, sane - I simply couldn't get it to work!
I've reached a point where hpoj seems to be running and the device is recognized successfully:

> 
$ sudo ptal-devid mlc:usb:PSC_2200_Series

MFG:Hewlett-Packard;MDL:PSC 2200 Series;CMD:MLC,PCL,PML,DW-PCL,DYN;CLS:PRINTER;1284.4DL:4d,4e,1;SN:MY29PD33GZ0G;S:0380008084021000002c1480048c250001c;AiO:0;


And:

> 
 $ sudo sane-find-scanner

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2911 [PSC 2200 Series]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.



BUT:
> 
$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


Obviously xsane can't find any devices!!! :(

My user is in the scanner group, and hpoj is uncommented in the dll file...

1. What am I doing wrong?!
2. Is there anything else I can try?
3. Has anyone here managed to scan with the PSC2210?

Thanks for your help!

---

### Post by emperor on 2005-03-19
See if "scanimage -L" works if you are positioned in the "/etc/sane.d" directory; either as root or a user.

---

### Post by kleeman on 2005-03-19
Try running as root (sudo xsane)
If that works it is a permissions issue
To fix permissions problems quickly issue:
sudo chmod a+rw /proc/bus/usb/*/*
To fix permanently create /etc/init.d/local with the following contents:
#! /bin/sh
chmod a+rw /proc/bus/usb/*/*

---

### Post by Avi on 2005-03-26
Thanks for this suggestion guys,
but neither of your tips helped..!  :-( 
The results were the same, no matter if user or root, or if in sane.d or not - No devices found!

Anyone else has a suggestion?
This is getting really frustrating!

Thanks

---

### Post by kleeman on 2005-03-26
What does lsusb show?

---

### Post by JoWilly on 2005-03-26
The only thing I do to get it working is:

1. sudo ptal-init setup (detect and install the usb PSC_2200)
2. reboot (If you do not reboot it does not work)
3. start xsane... it works...

---

### Post by Avi on 2005-03-30
lsusb shows:

```

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:008c Microsoft Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 03f0:2911 Hewlett-Packard
Bus 001 Device 001: ID 0000:0000

``` 

.. Now what..?  :sad:

---

### Post by emperor on 2005-03-30
On warty, I found I had that the USB device deamons were not starting up automaticly at boot-up. A work-around was to unplug the USB cable and then plug it back in, letting hotplug run the startup script, which worked.  This "problem" is fixed in Hoary.

---

### Post by kleeman on 2005-03-30
According to this page

[http://hpoj.sourceforge.net/suplist.shtml](http://hpoj.sourceforge.net/suplist.shtml)

your psc is supported under linux by the hpoj driver from hp which should interface with sane. Do you have the hpoj package installed? 

Assuming you do  :razz: and you have the 0.91 version (hoary) then this is a troubleshooter from hp:

[http://hpoj.sourceforge.net/hpoj-0.91/doc/setup-scan.html](http://hpoj.sourceforge.net/hpoj-0.91/doc/setup-scan.html)

Let us know if any of this helps....

---

### Post by Avi on 2005-04-02
Yes - I went through this web site, and others as well, and it didn't help me.. :-(

It's pretty clear, I think, there's not much more that can be done at this stage - 
I'm planning to re-install everything the day Hoary comes out, so I'm hoping that would be the solution... :-)

Thanks all!

---

