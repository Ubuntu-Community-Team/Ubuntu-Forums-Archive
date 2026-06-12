---
title: "scanimage finds my webcam but not my scanner"
date: 2008-08-18
forum: General Help
---

### Post by x20mar on 2008-08-18
Hi there,

I recently installed all the drivers for my scanner (epson 4490) and when I run sane-find-scanner I get

```
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:005:011
found USB scanner (vendor=0x03f0 [HP], product=0xbb02 [Photosmart 8400 series]) at libusb:005:007

```

(note the photosmart is a printer) and I've added the following line to epkowa.conf
```
usb 0x04b8 0x0119
```

However if I run scanimage -L, I get the following output
```
device `v4l:/dev/video0' is a Noname Chicony USB 2.0 Camera virtual device

```

Any suggestions?

Many Thanks

---

### Post by gobbles414 on 2008-08-18
So, you're not able to use your scanner in programs like XSane? I suggest that you go into Synaptic and install *gscan2pdf* (with all recommended packages) and *libsane-extras*. Restart your computer, then, try to scan using gscan2pdf.

Let me know if this helps.

---

### Post by x20mar on 2008-08-18
Hi gobbles thanks for getting back to me.

I tried reinstalling libsane-extras and gscan2pdf however after all that gscan2pdf can only see the webcam too!

Any other suggestions?

Thanks

---

### Post by gobbles414 on 2008-08-18
Is it possible for you to disconnect your webcam from your computer, then restart Ubuntu and try scanning again? This will tell us if the webcam is interfering with the scanner, or if drivers for your scanner are the source of the malfunction. Also, I just want to confirm that your scanner is the one listed [here]("http://www.epson.com/cgi-bin/Store/consumer/consDetail.jsp?oid=53540925").

---

### Post by x20mar on 2008-08-18
Hi,

I'm afraid that I can't disconnect my webcam as it is integrated into my laptop, but yeah that is my scanner. And before you ask, yes I did my driver for it from [http://www.avasys.jp/english/linux_e/dl_scan.html]("http://www.avasys.jp/english/linux_e/dl_scan.html") and I followed the instructions listed at [http://ubuntuforums.org/archive/index.php/t-587371.html]("http://ubuntuforums.org/archive/index.php/t-587371.html") (third post).

Thanks

---

### Post by gobbles414 on 2008-08-18
> ...and I followed the instructions listed at [http://ubuntuforums.org/archive/index.php/t-587371.html](http://ubuntuforums.org/archive/index.php/t-587371.html) (third post). I assume that you read in that link that there's an extra couple of steps required to get your scanner working in Ubuntu 8.04? Otherwise, I'm at a loss to understand why the procedure you cited isn't working for you.

---

### Post by x20mar on 2008-08-20
Yeah I doubled checked that and it was fine. Now here's the funny thing, I can use my scanner but only if I use the iscan software. So it works, just not in the way it's supposed to!

Oh well

---

### Post by gobbles414 on 2008-08-21
That's very strange indeed. Perhaps your issue will be resolved in the next version of Ubuntu, and/or with the next major update of the Linux Kernel.

---

### Post by Potters Son on 2009-12-05
I had a similar problem when I tried to use my HP Deskjet printer-scanner combo. XSANE would only find my webcam, and then complain when it didn't know how to use it. I believe that when XSANE finds a device it doesn't have any sort of driver for, it doesn't complain; it just silently ignores it. So, I was getting frustrated because I thought my webcam was throwing XSANE off from finding my scanner, but I really didn't have the drivers installed. Have you checked that the SANE backend supports your scanner? Or that you have the correct driver installed?

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

---

