---
title: "Problem with USB Printer in Ubuntu"
date: 2009-10-12
forum: Hardware
---

### Post by fcoster on 2009-10-12
Hey Folks,

I am setting up a new computer with the 9.10 Beta and am having some trouble getting my HP Laserjet 6P printer set up. My new motherboard doesn't have a parallel port, so I'm using a parallel-to-USB cable to connect the printer to the MB.

I have the various HP printer packages installed, but the Printer Configuration tool does not detect the printer (it's on and hooked up via USB).

The relevant dmesg seems to be:
```

[  186.296742] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  186.303452] usb[1860]: segfault at 0 ip 00528e63 sp bfebf924 error 4 in libc-2.10.1.so[4b4000+13e000]
[  275.748783] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  275.755711] usb[1910]: segfault at 0 ip 0035be63 sp bf863b84 error 4 in libc-2.10.1.so[2e7000+13e000]

```
Any thoughts? (One other thing: I am running 32bit Ubuntu 9.10Beta, but on a 64Bit Athlon chip--a fact that has already caused some trouble with Tweetdeck.... and that segfault makes me wonder).

---

### Post by koma77 on 2009-11-12
I started to get the same segfault in various processes seemingly at random when upgrading to 9.10.

For example:
kernel: [ 2891.050533] evolution-data-[6390]: segfault at a ip b6bac9fb sp b5afec50 error 4 in libc-2.10.1.so[b6b3f000+13e000]

or

glxinfo[6991]: segfault at bf8ad000 ip b76a4006 sp bf8a2d28 error 6 in libc-2.10.1.so[b762f000+13e000]


Maybe it is the same root cause... Did you find out what the problem was in your case?

---

### Post by fcoster on 2009-12-16
Just found the solution to this problem in this thread:
[http://ubuntuforums.org/showthread.php?t=1320742]("http://ubuntuforums.org/showthread.php?t=1320742")

Add a new printer, and specific as device URI:
parallel:/dev/usb/lp0

HUGE Kudos to fivenote who hunted down the bug.

---

