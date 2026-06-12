---
title: "Microsoft Wireless Optical Desktop stopped working in Jaunty after update"
date: 2009-06-27
forum: Hardware
---

### Post by lordelph on 2009-06-27
I was successfully using a Microsoft Wireless Optical Keyboard+Mouse in Jaunty until I performed an apt-get upgrade and rebooted. Now it no longer works. 

Here's some information that may aid someone more knowledgable than I in diagnosing it. If there's more info I can dig up, I'm happy to provide it:

```

# uname -a
Linux darth 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux
```

/var/log/dmesg contained a lot of messages related to the device, as well as a stack trace from another module which might be useful. I've pasted an example at [http://pastebin.com/f61db1f01](http://pastebin.com/f61db1f01)

Here's the packages I installed -one of these triggered the changed behaviour (one of the kernel ones I guess)

```
app-install-data-commercial11.9.04.2
app-install-data-partner11.9.04.2
compiz1:0.8.2-0ubuntu8.1
compiz-core1:0.8.2-0ubuntu8.1
compiz-gnome1:0.8.2-0ubuntu8.1
compiz-plugins1:0.8.2-0ubuntu8.1
compiz-wrapper1:0.8.2-0ubuntu8.1
file4.26-2ubuntu4
firefox3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.03.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0-branding3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0-gnome-support3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-gnome-support3.0.11+build2+nobinonly-0ubuntu0.9.04.1
gstreamer0.10-plugins-good0.10.14-1ubuntu0.1
gstreamer0.10-pulseaudio0.10.14-1ubuntu0.1
gvfs1.2.2-0ubuntu2
gvfs-backends1.2.2-0ubuntu2
gvfs-bin1.2.2-0ubuntu2
gvfs-fuse1.2.2-0ubuntu2
hal0.5.12~rc1+git20090403-0ubuntu3
libaprutil11.2.12+dfsg-8ubuntu0.1
libc62.9-4ubuntu6
libdecoration01:0.8.2-0ubuntu8.1
libgvfscommon01.2.2-0ubuntu2
libhal10.5.12~rc1+git20090403-0ubuntu3
libhal-storage10.5.12~rc1+git20090403-0ubuntu3
libmagic14.26-2ubuntu4
libmapnik0.50.5.1-3ubuntu2.1
libmapnik-dev0.5.1-3ubuntu2.1
libsasl2-22.1.22.dfsg1-23ubuntu3.1
libsasl2-modules2.1.22.dfsg1-23ubuntu3.1
libssl0.9.80.9.8g-15ubuntu3.2
libssl-dev0.9.8g-15ubuntu3.2
linux-generic2.6.28.13.17
linux-headers-2.6.28-132.6.28-13.44
linux-headers-2.6.28-13-generic2.6.28-13.44
linux-headers-generic2.6.28.13.17
linux-image-2.6.28-13-generic2.6.28-13.44
linux-image-generic2.6.28.13.17
linux-libc-dev2.6.28-13.44
linux-restricted-modules-2.6.28-13-generic2.6.28-13.17
linux-restricted-modules-common2.6.28-13.17
linux-restricted-modules-generic2.6.28.13.17
man-db2.5.5-1build1
mapnik-plugins0.5.1-3ubuntu2.1
menu2.1.41ubuntu1
menu2.1.41ubuntu1
openssl0.9.8g-15ubuntu3.2
python-cupshelpers1.1.3+git20090218-0ubuntu19.2
python-mapnik0.5.1-3ubuntu2.1
python-support0.8.7ubuntu4
python-support0.8.7ubuntu4
screen-profiles1.44-0ubuntu1.2
system-config-printer-common1.1.3+git20090218-0ubuntu19.2
system-config-printer-gnome1.1.3+git20090218-0ubuntu19.2
thunderbird2.0.0.22+build1+nobinonly-0ubuntu0.9.04.1
tzdata2009j-0ubuntu0.9.04
tzdata-java2009j-0ubuntu0.9.04
xserver-xorg-video-intel2:2.6.3-0ubuntu9.3
xulrunner-1.91.9.0.11+build2+nobinonly-0ubuntu0.9.04.1
xulrunner-1.9-gnome-support1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1
```

Anyone any pointers on how I might resolve this?

---

### Post by lordelph on 2009-06-27
Booting into kernel 2.6.27-11-generic made it work. Would still be interested to know how to get it working with the latest kernel though

---

### Post by thenanodude on 2009-08-06
I am also having the same problem.  Under Hardy, I could get my Microsoft Wireless Optical Desktop 3.0 working by using the kernel patch detailed in another post and re-compiling:

[http://ubuntuforums.org/showpost.php?p=3792455&postcount=6](http://ubuntuforums.org/showpost.php?p=3792455&postcount=6)

this patch was applied to /usr/src/linux/drivers/hid/usbhid/hid-quirks.c under Hardy.

However, after upgrading to Jaunty, I can not get my Desktop to work.  :(  It seems that the patch was applied to the newer kernels, however, the information is no longer in /usr/src/linux/drivers/hid/usbhid/hid-quirks.c but has been placed in a few files one directory down:

/usr/src/linux/drivers/hid/hid-core.c
/usr/src/linux/drivers/hid/hid-ids.h 
/usr/src/linux/drivers/hid/hid-microsoft.c

even though the patch appears to have been included in kernel 2.6.28, it doesn't seem to be working.  Can you check through the relevant files in the source code of the kernel you are using now to see how it is set up?

Incidentally, I have discovered that this problem is only relevant to earlier versions of the Desktop 3.0.  I own 2 of these, purchased about one year apart.  Even though the version numbers are identical on all the pieces, the first Desktop I bought requires the kernel patch, but the second one works without it!

---

### Post by thenanodude on 2009-08-06
Update:  After looking in the output from dmesg, I have determined that the "earlier" version of the Microsoft Wireless Optical Desktop "3.0" that does not work in kernel 2.6.28 is actually a Microsoft Wireless Optical Desktop 2.10!  My "later" version is a Microsoft Wireless Optical Desktop 2.2, and this one DOES work.

The 2.10 Desktop appears to be going through a cycle of connecting and disconnecting.  Here is a portion of the dmesg output:

```
[ 1471.708046] usb 2-5: new low speed USB device using ohci_hcd and address 2
[ 1471.875444] usb 2-5: configuration #1 chosen from 1 choice
[ 1473.115643] usbcore: registered new interface driver hiddev
[ 1473.115914] usbcore: registered new interface driver usbhid
[ 1473.115920] usbhid: v2.6:USB HID core driver
[ 1473.144648] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input10
[ 1473.176414] microsoft 0003:045E:009D.0001: input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:0b.0-5/input0
[ 1473.201185] usb 2-5: USB disconnect, address 2
[ 1473.207653] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input11
[ 1473.269339] microsoft 0003:045E:009D.0002: input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:0b.0-5/input1
[ 1473.980048] usb 2-5: new low speed USB device using ohci_hcd and address 3
[ 1474.147448] usb 2-5: configuration #1 chosen from 1 choice
[ 1474.157969] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input12
[ 1474.190354] microsoft 0003:045E:009D.0003: input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:0b.0-5/input0
[ 1474.219142] usb 2-5: ctrl urb status -62 received
[ 1474.220145] usb 2-5: ctrl urb status -62 received
[ 1474.221140] usb 2-5: ctrl urb status -62 received
[ 1474.222125] usb 2-5: ctrl urb status -62 received
[ 1474.223138] usb 2-5: ctrl urb status -62 received
[ 1474.224138] usb 2-5: ctrl urb status -62 received
[ 1474.225132] usb 2-5: ctrl urb status -62 received
[ 1474.226126] usb 2-5: ctrl urb status -62 received
[ 1474.226999] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input13
[ 1474.285422] microsoft 0003:045E:009D.0004: input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:0b.0-5/input1
[ 1474.285766] usb 2-5: USB disconnect, address 3

```

Unfortunately, I have no idea how to fix this...

---

