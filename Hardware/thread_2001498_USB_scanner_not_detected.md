---
title: "USB scanner not detected"
date: 2012-06-11
forum: Hardware
---

### Post by TheBigH on 2012-06-11
Hi everyone,
I am trying to get a Lexmark X1150 printer/scanner to work on Lubuntu. I have got the printing part of it to work, but the scanning still doesn't.

I've installed Xsane version 0.998, and the sane back-ends according to the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1915316](http://ubuntuforums.org/showthread.php?t=1915316)

Unfortunately it is still unable to detect the scanner.

lsusb shows it's there, but neither "scanimage -L" nor "sane-find-scanner" are able to detect it, even when I run them as root. This is the error message I get from sane-find-scanner.
```

# No USB scanners found. If you expected something different, make sure that
# you have loaded a kernel driver for your USB host controller and have setup
# the USB system correctly. See man sane-usb for details.
# SANE has been built without libusb support. This may be a reason
# for not detecting USB scanners. Read README for more details.
```How can I get the computer to detect the scanner?
Thanks.[FONT=monospace]
[/FONT]

---

### Post by TheBigH on 2012-06-14
Bump. Can anyone help me with this?

---

### Post by TheBigH on 2012-06-21
Bump.

---

### Post by Ravi5kumar on 2012-06-22
Hi, may be this will link help you! [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

