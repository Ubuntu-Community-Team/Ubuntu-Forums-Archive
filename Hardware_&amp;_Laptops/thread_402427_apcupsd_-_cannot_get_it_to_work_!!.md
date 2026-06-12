---
title: "apcupsd - cannot get it to work !!"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by neill on 2007-04-05
hi

i'm pulling my hair out here trying to get my APC UPS (BackUPS CS 500 with the RJ45 to USB cable) recognized by edgy

i've installed apcupsd with synaptic OK

i've edited /etc/apcupsd/apcupsd.conf as follows

UPSCABLE usb
UPSTYPE usb
DEVICE
..
..
NETSERVER ON
NISIP 127.0.0.1
NISPORT 3551

/etc/init.d/acupsd start give me "Starting APC UPS power management"

but in var/log/apcupsd/events i get "PANIC: cannot recognize UPS via serila port"

so i ran (as sudo) ./make-hiddev in /usr/share/doc/apcupsd/examples - as suggested elsewhere in this forum - and the appropriate files (/dev/usb/hid/hiddev0 etc) exist

**still no joy**

by which i mean no nice messages in the log and apcupsd status give me a connection refused error on localhost:3551

i'm at a loss now :confused:

anyone any suggestions ??

thanks

neill

---

### Post by tgalati4 on 2007-04-08
The RJ45 cable is actually a serial cable interface. The USB is used for a real USB interface.  Try a different cable type for UPSCABLE.
 
You may need to force the PL2303 module if it doesn't load automatically.  Check lsmod to determine what gets loaded after you plug it in.

---

### Post by neill on 2007-04-09
fixed it - by accident !!

i'd made some 'security enhancements' to /etc/fstab so /var was now mounted as noexec, nosuid and nodev (as i recall)

when i changed them all back to defaults - ta da - it worked :) 

now i can turn off the power and i get a graceful shutdown from the UPS and all the right messages

thanks for the help anyway

neill

---

### Post by theQmaster on 2007-06-18
Figure it out ? I had it running fine in 5.04 and I moved to 6.10 via 5.10 and 6.06 and now I get the same message and my server doesn't start.

---

### Post by yowshi on 2007-08-16
i have a problem where my UPS isnt APC and the apc monitor refuses to see it. is there another UPS monitor for ubuntu that is more generic?

---

