---
title: "Is the Officejet HP 4500 compatible with Ubuntu linux?"
date: 2011-01-03
forum: Hardware
---

### Post by honeybear on 2011-01-03
Hello,

I would like to know if it works with Ubuntu. Is there some user xperience? 

many thanks

---

### Post by ajgreeny on 2011-01-03
Looks like it works fully, like most HPs.  Unfortunately the hplip [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) site is offline at the moment and has been over Christmas and New Year, but it is usually a good site for info.

See [http://www.openprinting.org/printer/HP/HP-Officejet-4500-G510n-z](http://www.openprinting.org/printer/HP/HP-Officejet-4500-G510n-z)

---

### Post by honeybear on 2011-01-04
how to scan? scanimage finds nothing ... 

```
a# sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x2d12 [Officejet 4500 G510g-m]) at libusb:002:011
found USB scanner (vendor=0x066f [ Sigmatel Inc ], product=0x4200 [ IrDA/USB Bridge]) at libusb:001:006
found USB scanner (vendor=0x045e, product=0x0719) at libusb:001:004
found USB scanner (vendor=0x1a86, product=0x7523 [USB2.0-Ser!]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
root@dlinux05:/home/honey# scanimage -L
device `v4l:/dev/video1' is a Noname Pinnacle PCTV Stereo (saa7134) virtual device
device `v4l:/dev/video0' is a Noname UVC Camera (046d:0807) virtual device

```

---

### Post by unclefrancis on 2011-01-06
> **honeybear said:**
> Hello,

I would like to know if it works with Ubuntu. Is there some user xperience? 

many thanks

I just bought an officejet hp 4500 today. All I did was connect it to my laptop via usb (cable not included) and it was good to go. I'm running ubuntu 10.10.

---

### Post by hudo on 2011-05-11
Hello, 

I have connected the officejet 4500 to ethernet and everything works fine (print, scan, fax). I've installed the device with help of the hp device manager ( command from terminal: hp-toolbox )

Drivers are from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

A good howto is [http://www.youtube.com/watch?v=v3rxpX2cgtM](http://www.youtube.com/watch?v=v3rxpX2cgtM)

So I would say, yes it is compatible with Ubuntu Linux, at least with 10.05 (lucid).

---

