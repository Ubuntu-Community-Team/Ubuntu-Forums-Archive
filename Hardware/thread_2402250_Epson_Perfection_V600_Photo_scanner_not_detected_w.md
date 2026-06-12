---
title: "Epson Perfection V600 Photo scanner not detected with Vuescan"
date: 2018-09-27
forum: Hardware
---

### Post by trash1464 on 2018-09-27
A fresh install of 18.04.0 LTS has broken the subject scanner function except when Vuescan is launched with root privileges:

```
rich@rich-Linux:~/Vuescan$ sudo ./vuescan
[sudo] password for rich: 
Gtk-Message: 15:02:44.047: Failed to load module "canberra-gtk-module"


(vuescan:31145): IBUS-WARNING **: 15:02:44.332: The owner of /home/rich/.config/ibus/bus is not root! 

```

All requisite drivers look to be in place and were installed via Epsons linux driver package but the scanner is not detected when Vuescan is launched normally. 
```
lsusb
Bus 003 Device 003: ID 04b8:013a Seiko Epson Corp. GT-X820 [Perfection V600 Photo]

```
This was working in 16/04 but I cannot remember how I did it. 

I dont think I am the only one to ever encounter this issue. Can you help?

---

### Post by edadasiewicz on 2018-09-28
I have the same scanner/software running OK under 18.04.  I do have the following packages installed libcanberra-gtk3-module and libcanberra-gtk-module.  Also, I run vuescan as a normal user.  The vuescan in /usr/bin is a shell script which exec's the vuescan in /opt/vuescan, all of which are executable by me.  I also have iscan installed with iscan-plugin-gt-x820.

---

### Post by trash1464 on 2018-09-28
> **edadasiewicz said:**
> I have the same scanner/software running OK under 18.04.  I do have the following packages installed libcanberra-gtk3-module and libcanberra-gtk-module.  Also, I run vuescan as a normal user.  The vuescan in /usr/bin is a shell script which exec's the vuescan in /opt/vuescan, all of which are executable by me.  I also have iscan installed with iscan-plugin-gt-x820.

Interesting! I do not have a vuescan script in /usr/bin. Did you write that script?

---

### Post by slickymaster on 2018-09-28
*Thread moved to **Hardware**.*

---

### Post by edadasiewicz on 2018-09-28
It only contains 3 lines:

#!/bin/sh
cd /opt/vuescan
exec ./vuescan "$@"

If I wrote it them I borrowed it from somewhere (I used to run Arch Linux) since I always start my scripts with

#!/usr/bin/env bash

---

### Post by trash1464 on 2018-09-28
> **edadasiewicz said:**
> It only contains 3 lines:

#!/bin/sh
cd /opt/vuescan
exec ./vuescan "$@"

If I wrote it them I borrowed it from somewhere (I used to run Arch Linux) since I always start my scripts with

#!/usr/bin/env bash

Thanks, I tried that but it did not solve the issue. 

Just a thought, since Vuescan runs OK as root but not OK as a user, it seems to be a permissions issue but permissions to what? Thats the question I am struggling with.

---

### Post by edadasiewicz on 2018-09-29
I created the script so that I could call it from vuescan.desktop in /usr/share/applications.  If I try to start vuescan as root (via sudo) I get the same error as you indicated but vuescan still starts.

If you try to run vuescan as a normal user do you get any error messages?  Does sane-find-scanner find your Epson?  Running the app as a normal user shows a bunch of "access denied" errors but it still should find the scanner.

---

### Post by trash1464 on 2018-09-29
> **edadasiewicz said:**
> I created the script so that I could call it from vuescan.desktop in /usr/share/applications.  If I try to start vuescan as root (via sudo) I get the same error as you indicated but vuescan still starts.

If you try to run vuescan as a normal user do you get any error messages?  Does sane-find-scanner find your Epson?  Running the app as a normal user shows a bunch of "access denied" errors but it still should find the scanner.

You are correct a series of errors returns from sane-find-scanner:

```
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x8002 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 008:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x0a12/0x0001 at 005:003: Access denied (insufficient permissions)
could not open USB device 0x2109/0x3431 at 005:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x800a at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x0835/0x8502 at 003:012: Access denied (insufficient permissions)
could not open USB device 0x0835/0x8500 at 003:011: Access denied (insufficient permissions)
could not open USB device 0x13ba/0x0018 at 003:010: Access denied (insufficient permissions)
could not open USB device 0x0d8c/0x000e at 003:009: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc50e at 003:008: Access denied (insufficient permissions)
could not open USB device 0x0835/0x8501 at 003:007: Access denied (insufficient permissions)
could not open USB device 0x0835/0x8500 at 003:006: Access denied (insufficient permissions)
could not open USB device 0x0409/0x02b9 at 003:004: Access denied (insufficient permissions)
could not open USB device 0x0409/0x005a at 003:002: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc52b at 003:005: Access denied (insufficient permissions)
could not open USB device 0x04b8/0x013a at 003:003: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Running Vuescan as a normal user does not return errors, it finds a network attached Epson scanner but not the USB attached scanner. Running Vuescan as root finds network as well as USB attached scanners. Similarly, running sane-find-scanner as a user does not find USB attached scanner and running sane-find-scanner as root does find the USB scanner. The question then is how to assign access permissions to USB ports?

---

### Post by edadasiewicz on 2018-09-30
Check out this link [http://ask.xmodulo.com/change-usb-device-permission-linux.html]("http://ask.xmodulo.com/change-usb-device-permission-linux.html")

I know that I have a similar file in /etc/udev/rules.d.

---

### Post by trash1464 on 2018-10-01
> **edadasiewicz said:**
> Check out this link [http://ask.xmodulo.com/change-usb-device-permission-linux.html](http://ask.xmodulo.com/change-usb-device-permission-linux.html)

I know that I have a similar file in /etc/udev/rules.d.

Thanks again. I followed the instructions in that link with high hopes but in the end the problem persists. So the search goes on.

---

### Post by smsmith050 on 2019-02-02
The problem is discussed in this bug report.
I followed the instructions on comment 196 

I did not use the sudo cp /usr/lib/sane/libsane-epk* /usr/lib/x86_64-linux-gnu/sane/

I used sudo ln -sfr /usr/lib/sane/libsane-epkowa* /usr/lib/x86_64-linux-gnu/sane

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/196](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1728012/comments/196)

My scanner is working at the moment.

---

### Post by smsmith050 on 2019-02-16
Epson V600 stopped working with vuescan today.

iscan the simple utility from epson still works. 

I did allow the updates to ubuntu this morning. 

Anyone have vuescan working with the V600 and 18.04?

---

### Post by smsmith050 on 2019-02-16
scanimage works 

scanimage --format=tiff --x-resolution=400 --y-resolution=400   >a.tiff

---

### Post by him610 on 2019-02-16
If you want to find your scanner, don't use *sane-find-scanner* , instead use *scanimage -L*

---

### Post by smsmith050 on 2019-02-17
The scanner stops working with the blue light flashing if I try 16 bit scan.

scanimage --format=tiff --x-resolution=200 --y-resolution=200 --depth=16  >16.tiff

The scanner also stops working if I try 16bit scans from xsane or gimp.

I have only done 16bit scans with vuescan but vuescan has trouble detecting the V600. The vuescan log shows Epson Plugin entry points not found: /usr/lib/iscan/libesintA1.so

Has anyone been able to make 16bit scans with the V600 using scanimage?

---

### Post by brian_p on 2019-02-17
If 'sane-find-scanner' doesn't give a sensible ouput, neither will 'scanimage -L'. With a USB connection, use both.

---

### Post by smsmith050 on 2019-02-27
On my system vuescan will launch and find the epson V600 if I unplug and plug the usb cable to the scanner before I launch vuescan.

---

