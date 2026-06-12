---
title: "DSLR Canon EOS 400D / Rebel XTI [Resolved]"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by endtroducing on 2007-03-03
Version: Ubuntu Edgy 6.10

Problem: Canon EOS 400D / Rebel XTI is not supported after install.

Resolution:

Open a terminal and redirect output to a text file:

```
for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done > /home/yourusername/udevinfo.txt
```

Open the udevinfo.txt and search for canon

It will look like this: 

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb5/5-5':
    ID=="5-5"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{product}=="Canon Digital Camera"
    SYSFS{manufacturer}=="Canon Inc."
    SYSFS{maxchild}=="0"
    SYSFS{version}==" 2.00"
    SYSFS{devnum}=="7"
    SYSFS{speed}=="480"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bcdDevice}=="0002"
    SYSFS{idProduct}=="3110"  <--------
    SYSFS{idVendor}=="04a9"   <--------
    SYSFS{bMaxPower}=="  2mA"
    SYSFS{bmAttributes}=="c0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

Open /etc/udev/rules.d/45-libgphoto2.rules

```
sudo nano -w /etc/udev/rules.d/45-libgphoto2.rules
```

Add the following lines at the bottom of the file, just before LABEL="libgphoto2_rules_end"

SYSFS{idVendor}=="YOURIDVENDOR", SYSFS{idProduct}=="YOURIDPRODUCT", MODE="0660", GROUP="plugdev"

For me it was:

SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3110", MODE="0660", GROUP="plugdev"

Restart udev

```
sudo /etc/init.d/udev restart
```

---

### Post by towsonu2003 on 2007-03-15
Would this work on Dapper with other cams as well? I bought a Canon G7 (supported by a later version of gphoto) and I'm wondering whether your instructions would work for me, or would I be borking my install? Thanks :)

---

### Post by soan on 2007-04-03
Thanx very much for this. This helped alot. 

Got my Canon 400D working with digikam.

---

### Post by Bluejacket on 2007-04-12
My Canon 400D worked with digikam 0.8.2-rc1 on Kubuntu 6.06 straight away. I simply clicked Camera -> Add camera, and I can download pictures with the USB cable. Digikam lists it as USB PTP Class camera but everything works fine.

---

### Post by Timokl on 2007-12-21
> **Bluejacket said:**
> My Canon 400D worked with digikam 0.8.2-rc1 on Kubuntu 6.06 straight away. I simply clicked Camera -> Add camera, and I can download pictures with the USB cable. Digikam lists it as USB PTP Class camera but everything works fine.

It also works out of the box with Ubuntu (Gnome and gThumb).

---

