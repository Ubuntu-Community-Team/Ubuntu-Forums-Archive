---
title: "SANE not detecting USB Canon ImageCLASS D420 scanner"
date: 2014-01-14
forum: Hardware
---

### Post by nathan15 on 2014-01-14
I've been struggling to make a Canon D420 scanner work. The printer part works fine. I've installed all the latest SANE and the backends, to my knowledge, but sane-find-scanner is still unable to locate the scanner. The relevant result is:

```
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.
```

Would the lack of libusb support be the culprit? If so, could somebody walk me through how to rebuild SANE with libusb support? I've tried a bit myself but can't figure it out. Sorry for being a bit of a newbie. I'm running 13.10 on an Asus Zenbook.

Thank you for your help!

---

### Post by nathan15 on 2014-01-18
Please help! By the way, I have libusb installed:

```
$ libusb-config --version
0.1.12
```

and 

```
$ sane-config --version
1.0.25

```

---

### Post by aikishugyo on 2014-01-21
Read the man page for sane-pixma to see if it is supported or not. You need 0.17.6, see the CVS SANE-supported scanners webpage for more details.

---

### Post by stephenbbb on 2014-01-21
contact the sane developers. look in the readme who exactly is working on the driver for your scanner and send him an email. 
I got help and the guy wrote a patch for me. he will ask you for output from diagnostic commands and may take a few iterations but it will get done.

---

### Post by aikishugyo on 2014-01-21
@stephenbbb: It is done, see my message above. It's up to the OP to figure out what he has installed.

---

### Post by jjmv99 on 2014-03-03
> **nathan15 said:**
> I've been struggling to make a Canon D420 scanner work. The printer part works fine. I've installed all the latest SANE and the backends, to my knowledge, but sane-find-scanner is still unable to locate the scanner. The relevant result is:

```
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.
```

Would the lack of libusb support be the culprit? If so, could somebody walk me through how to rebuild SANE with libusb support? I've tried a bit myself but can't figure it out. Sorry for being a bit of a newbie. I'm running 13.10 on an Asus Zenbook.

Thank you for your help!

hello, I am having the same problem can you share how you fixed it?
I only need the printer to work 
thanks

---

### Post by aikishugyo on 2014-03-03
> **jjmv99 said:**
> hello, I am having the same problem can you share how you fixed it?
I only need the printer to work 
thanks
I think you should start your own thread: SANE is scanning software, you need something different for printing.

---

