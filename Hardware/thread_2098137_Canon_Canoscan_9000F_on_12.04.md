---
title: "Canon Canoscan 9000F on 12.04"
date: 2012-12-25
forum: Hardware
---

### Post by rob150588 on 2012-12-25
Good evening/happy holidays !

We have receive a new scanner in the household (as title); and it has fallen to the resident IT 'expert' (me) to get the thing running.

It was selected as it was listed on SANE as having 'complete compatibility'. - sounds too good to be true ?!

I have been following what was detailed on this *[COLOR="Navy"][thread]("http://ubuntuforums.org/showthread.php?t=2072162")[/COLOR].*

Following the instructions and installing the 1.0.23 backends from the linked site causes the sane-backends to stop funtioning completely, i.e. sane-find-scanner - base: no such file or directory, etc.

So...back to basics. I have followed the official instructions from ***[B]this [COLOR="Navy"][link]("https://help.ubuntu.com/community/CompileSaneFromSource")[/COLOR].**[/B]*

This at least gets sane up and running again.

The scanner has been plugged in and is detected on lsusb:
*Bus 002 Device 007: ID 04a9:1908 Canon, Inc.*

sane-find-scanner output:
found USB scanner (vendor=0x04a9 [Canon], product=0x1908 [CanoScan]) at libusb:002:007

So far so good. Permissions are set correctly with udev, so the ordinary user should be able to use it.

However - scanimage -L output:
*No scanners were identified. If you were expecting something different...blah, blah, blah.*

To the uninitiated eye (mine) this is obviously not working.

I note that there are version mismatches with the output from scanimage -V:
*scanimage (sane-backends) 1.0.24git; backend version 1.0.22*

...but with no amount of fiddling can I change this.

Does anyone out there have an idea why this is happening and how I can go about getting this to work ?

Any help is much appreciated.

Rob.

---

### Post by rob150588 on 2012-12-26
Bump.

---

### Post by rob150588 on 2012-12-29
Bump.

---

