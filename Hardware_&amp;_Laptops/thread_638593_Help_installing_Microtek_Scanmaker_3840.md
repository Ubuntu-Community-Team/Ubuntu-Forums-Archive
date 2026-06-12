---
title: "Help installing Microtek Scanmaker 3840"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by ramontayag on 2007-12-12
Hey everyone. I use Ubuntu for web development but not very good at compiling stuff.  I need the community's help now.  I saw other threads that touched on installing this scanner on Ubuntu, but I tried those and they didn't work for me.

Ubuntu: 7.10
Scanner: Microtek ScanMaker 3840

```
sudo xsane
``` gives me

> Failed to open device 'sm3840:libusb:002:003: Access to resource has been denied.

Normally, running that as root fixed the problem for people and they simply had to ```
sudo chmod /dev/bus/usb/002/003
``` or ```
sudo chmod a+w /dev/bus/usb/002/003
``` but that doesn't work since I can't even access it as root.

Other stuff that might give you guys clues as to what's wrong (these are just commands and results):
```
tayag@tayag-desktop:~$ lsusb
Bus 001 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05da:30d4 Microtek International, Inc. 
Bus 002 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 001: ID 0000:0000  

```

```
tayag@tayag-desktop:~$ sudo scanimage -T
scanimage: open of device sm3840:libusb:002:003 failed: Access to resource has been denied

```

```
tayag@tayag-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05da, product=0x30d4 [USB Scanner]) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

Thank you!!

---

### Post by ramontayag on 2007-12-22
Any ideas so far? :)

---

### Post by shinkaide on 2007-12-24
Man, I have the same scanner and the same problem.  It's frustrating for me because I had no problems getting it to work out of the box with 6.06. Ever since I installed 7.10, I haven't been able to get part of my work done (I'm a comic artist), so now I'm basically just piling up pencilled pages...

Not able to get much of a response here at the forums either... :(

---

### Post by ramontayag on 2008-01-09
Aww.. shucks.  I'll have to remove ubuntu now and reinstall windows just to get the scanner to work? :(

---

### Post by alienexplorers on 2008-05-17
The sm3840 driver is bad you need the libsane-sm3840.so.1.0.15 driver. It works perfectly.

---

### Post by dgkalmegh on 2008-06-29
I have replaced it bt there is a problem that Now sane is saying no devices found

---

