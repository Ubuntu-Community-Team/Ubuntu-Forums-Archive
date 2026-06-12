---
title: "USB scanner not recognized anymore in 11.10 64bit (it was on 11.04 32bit)"
date: 2011-10-21
forum: Hardware
---

### Post by nandinga on 2011-10-21
Hi!

I had been successfuly using the scanner of my EPSON Stylus DX4250 on Ubuntu (32bit) since I've bought it years ago.

Now I've updated to 11.10 64bit and it is not working anymore.

Have heard of some issues regarding USB, and some others regarding HAL, but I'm not sure where to start looking.

Here is what dmesg shows:

```

[53778.567908] usb 2-1.2.4: new high speed USB device number 10 using ehci_hcd
[53779.874059] usb 2-1.2.4: usbfs: process 25525 (usb) did not claim interface 0 before use

```

Any idea?

---

### Post by nandinga on 2011-10-21
Doing a reboot, this is what I get from dmsg:

```
[   72.024538] usb 2-1.4: new high speed USB device number 6 using ehci_hcd
[   73.266142] show_signal_msg: 30 callbacks suppressed
[   73.266145] simple-scan[1972]: segfault at 9691a85 ip 00007f146f3131a4 sp 00007f145fffbe00 error 4 in libc-2.13.so[7f146f2ca000+195000]
[   73.322406] usb 2-1.4: usbfs: process 2027 (usb) did not claim interface 0 before use
[  146.794098] usb 2-1.4: USB disconnect, device number 6
```

That segfault of simple-scan was when I was trying to see if it was detected. An empty list showed.

---

### Post by digitalslave on 2011-10-22
did you download and install the 64bit linux driver?

---

### Post by kurt18947 on 2011-10-22
This may or may not be applicable to your situation but I'll mention it. I have a Brother that had a situation very much like you are having.  The scanner had worked perfectly in prior Ubuntu releases but not 11.10.  The problem turned out to be some files that were being copied to one folder when they should have been copied to another or both folders. Below is the link. Again, this is Brother not Epson but I wonder if Epson has something similar going on.  Maybe give you a place to start looking.  Good luck.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

### Post by nandinga on 2011-10-22
I hadn't, but did now, from avasys.jp (epson redirected me there). No luck :s

I never had the need to do that before (earlier versions on Ubuntu, and 32bit).

Sigh... too many changes on the two latest Ubuntu releases. Linux 3.0, Gnome 3, Unity... feels very unstable :(

Edit: this reply is for digitalslave. Next reply came while writing :p

---

### Post by nandinga on 2011-10-22
Thx kurt18947, I'll take a look.

---

