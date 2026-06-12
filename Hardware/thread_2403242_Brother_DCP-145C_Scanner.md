---
title: "Brother DCP-145C Scanner"
date: 2018-10-09
forum: Hardware
---

### Post by ruquay2 on 2018-10-09
Hello, I am having difficulties getting a Brother DCP-145C Scanner to work properly under Bionic Beaver. I downloaded the driver from the Brother website and followed the instructions exactly (for installing all-in-one), and the printer worked just fine. The scanner doesn't work, however.

After reading through lots of similar posts here, I tried the commands sane-find-scanner and scanimage. It seems that the scanner is available, but scanimage fails.

For lots of other similar models I have seen advice about editing the udev rules, but I will readily admit that I don't fully understand how these work, and the installed file from the Brother installation process seems to differ quite a bit from others I've seen. I would be grateful for any help or pointers about how to debug the problem or get the scanner working.

The file 60-brother-libsane-type1.rules file which was installed:

```
#
#   udev rules sample for Brother MFP
#         version 1.0.2-0
#
#   Copyright (C) 2012-2016 Brother. Industries, Ltd.
#
#   copy to /etc/udev/rules.d or /lib/udev/rules.d
#


ACTION!="add", GOTO="brother_mfp_end"


SUBSYSTEM=="usb", GOTO="brother_mfp_udev_1"
SUBSYSTEM!="usb_device", GOTO="brother_mfp_end"
LABEL="brother_mfp_udev_1"




SYSFS{idVendor}=="04f9", GOTO="brother_mfp_udev_2"
ATTRS{idVendor}=="04f9", GOTO="brother_mfp_udev_2"
GOTO="brother_mfp_end"
LABEL="brother_mfp_udev_2"


#  ATTRS{bInterfaceNumber}=="01", GOTO="brother_mfp_udev_3"
#  ATTRS{bInterfaceNumber}=="02", GOTO="brother_mfp_udev_3"
#  ATTRS{bInterfaceNumber}=="03", GOTO="brother_mfp_udev_3"
#  GOTO="brother_mfp_end"
#  LABEL="brother_mfp_udev_3"


ATTRS{bInterfaceClass}!="0ff", GOTO="brother_mfp_end"
ATTRS{bInterfaceSubClass}!="0ff", GOTO="brother_mfp_end"
ATTRS{bInterfaceProtocol}!="0ff", GOTO="brother_mfp_end"


#MODE="0666"
#GROUP="scanner"
ENV{libsane_matched}="yes"
#SYMLINK+="scanner-%k"




LABEL="brother_mfp_end"



```

Result of sane-find-scanner (normal user):

```



  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not open USB device 0x04f2/0xb044 at 002:004: Access denied (insufficient permissions)
could not open USB device 0x0781/0x5591 at 002:005: Access denied (insufficient permissions)
found USB scanner (vendor=0x04f9 [Brother], product=0x0206 [DCP-145C]) at libusb:002:003
could not open USB device 0x8087/0x0020 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0020 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

sane-find-scanner as root:

```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04f9 [Brother], product=0x0206 [DCP-145C]) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


```

And the result of scanimage is the same whether run as root or as a normal user:


```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

---

### Post by plucky on 2018-10-09
Have you installed sane-utils?

I think this is mentioned as one of the pre-requisites.

```
sudo apt install sane-utils
```

Then reboot

Good Luck

---

### Post by ruquay2 on 2018-10-10
Hello plucky and thanks for the tip. I have just tried that out and apparently I already have sane-utils installed (and newest version).

It seems to me that the scanner is detected by sane-find-scanner (whether as normal user or root), but for some reason scanimage does not work. I see the note that "the scanner may or may not be supported" and directions to read "the backend's man page", but I'm unsure what that means for me more concretely.

As a side note, also in the GUI Simple Scan program the scanner is not found.

Possibly unhelpful information: I am quite sure that this exact scanner was working with an earlier version of Ubuntu (previous LTS). However, I did not do an upgrade on this machine but a fresh install. Is it possible that support for this device has been dropped, or that there would be upgrades to the driver from the manufacturer that they have not implemented?

Thanks and would be most grateful for any tips on other things to try.

---

### Post by him610 on 2018-10-10
Hello ruquay2,

I own a Brother MFC-7360N that was installed in Xubuntu 18.04. After initially installing the Brother scan software, brscan4 and brscan, back in April when 18.04 was first released, the scan function worked as expected. After reading your post, I checked to see if the scan function still worked and discovered it does not. Using *scanimage -L* finds the scanner, but *simple scan* does not find it. The Brother software setup and *simple scan* does work using Xubuntu 16.04.5 on a different computer

I will see if I can figure it out and post results in this thread.

---

### Post by firarottico on 2018-10-10
> **ruquay2 said:**
> Hello, I am having difficulties getting a Brother DCP-145C Scanner to work properly under Bionic Beaver. I downloaded the driver from the Brother website and followed the instructions exactly (for installing all-in-one), and the printer worked just fine. The scanner doesn't work, however.

After reading through lots of similar posts here, I tried the commands sane-find-scanner and scanimage. It seems that the scanner is available, but scanimage fails.

For lots of other similar models I have seen advice about editing the udev rules, but I will readily admit that I don't fully understand how these work, and the installed file from the Brother installation process seems to differ quite a bit from others I've seen. I would be grateful for any help or pointers about how to debug the problem or get the scanner working.

The file 60-brother-libsane-type1.rules file which was installed:

```
#
#   udev rules sample for Brother MFP
#         version 1.0.2-0
#
#   Copyright (C) 2012-2016 Brother. Industries, Ltd.
#
#   copy to /etc/udev/rules.d or /lib/udev/rules.d
#


ACTION!="add", GOTO="brother_mfp_end"


SUBSYSTEM=="usb", GOTO="brother_mfp_udev_1"
SUBSYSTEM!="usb_device", GOTO="brother_mfp_end"
LABEL="brother_mfp_udev_1"




SYSFS{idVendor}=="04f9", GOTO="brother_mfp_udev_2"
ATTRS{idVendor}=="04f9", GOTO="brother_mfp_udev_2"
GOTO="brother_mfp_end"
LABEL="brother_mfp_udev_2"


#  ATTRS{bInterfaceNumber}=="01", GOTO="brother_mfp_udev_3"
#  ATTRS{bInterfaceNumber}=="02", GOTO="brother_mfp_udev_3"
#  ATTRS{bInterfaceNumber}=="03", GOTO="brother_mfp_udev_3"
#  GOTO="brother_mfp_end"
#  LABEL="brother_mfp_udev_3"


ATTRS{bInterfaceClass}!="0ff", GOTO="brother_mfp_end"
ATTRS{bInterfaceSubClass}!="0ff", GOTO="brother_mfp_end"
ATTRS{bInterfaceProtocol}!="0ff", GOTO="brother_mfp_end"


#MODE="0666"
#GROUP="scanner"
ENV{libsane_matched}="yes"
#SYMLINK+="scanner-%k"




LABEL="brother_mfp_end"



```

Result of sane-find-scanner (normal user):

```



  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not open USB device 0x04f2/0xb044 at 002:004: Access denied (insufficient permissions)
could not open USB device 0x0781/0x5591 at 002:005: Access denied (insufficient permissions)
found USB scanner (vendor=0x04f9 [Brother], product=0x0206 [DCP-145C]) at libusb:002:003
could not open USB device 0x8087/0x0020 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0020 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

sane-find-scanner as root:

```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04f9 [Brother], product=0x0206 [DCP-145C]) at libusb:002:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


```

And the result of scanimage is the same whether run as root or as a normal user:

[FONT=Arial][[COLOR=#000000]FetLife[/COLOR]]("https://fetlife.vip/")[/FONT]
[COLOR=#000000][CENTER][FONT=Arial]
[/FONT][/CENTER]
[/COLOR][URL="https://downloader.vip/imvu/"][COLOR=#000000][FONT=Arial]IMVU[/FONT]
[/COLOR][/URL][COLOR=#000000]
[/COLOR][URL="https://downloader.vip/canva/"][COLOR=#000000][FONT=Arial]Canva[/FONT]
[/COLOR][/URL]
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```
I possess a Brother MFC-7360N that was introduced in Xubuntu 18.04. After at first introducing the Brother examine programming, brscan4 and brscan, back in April when 18.04 was first discharged, the sweep work functioned of course. In the wake of perusing your post, I verified whether the sweep work still worked and found it doesn't. Utilizing scanimage - L finds the scanner, yet straightforward output does not discover it. The Brother programming setup and straightforward output works utilizing Xubuntu 16.04.5 on an alternate PC 


I will check whether I can make sense of it and post results in this string.

---

### Post by him610 on 2018-10-10
Re: Post #4

As I said before my MFC-7360N scanner has not been working either. I discovered there was a difference between the drivers installed on the LTS 16.04.5 system (with working scanner) and the LTS 18.04.1 system (with non-working scanner.) I completely removed the older driver from the LTS 18.04.1 system, transferred the more current, *brscan4-0.4.4-3.amd64.deb*, to the LTS 18.04.1 system, and installed the updated driver IAW the Brother installation instructions - it works.

I have successfully scanned a document from the Brother MFC-7360N to the LTS 18.04.1 system with the newly installed updated driver using *simple scan.*

By the way, the date of *brscan4-0.4.4-3.amd64.deb* is 2017-05-23.

Maybe, this will help other folks.

---

