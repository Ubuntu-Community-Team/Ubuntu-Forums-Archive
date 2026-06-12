---
title: "udev failure to run script with mypassport"
date: 2011-07-02
forum: Hardware
---

### Post by avdzm on 2011-07-02
Hey,

I'm having trouble with a udev trigger event.
I would like to sync some folders to my ext usb hdd every time it is connected.

looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2
  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-1':
    KERNELS=="2-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="1695"
    [B]ATTRS{idVendor}=="1058"
    ATTRS{idProduct}=="0730"[/B]
    ATTRS{bcdDevice}=="1015"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="45"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Western Digital"
    ATTRS{product}=="My Passport 0730"
    **ATTRS{serial}=="57584C314531315A4D533936"**

this is my udev rule file mypassport.rules
KERNEL=="sd*1",
ACTION=="add",
ATTRS{idVendor}=="1058",
ATTRS{idProduct}=="0730",
ATTRS{serial}=="57584C314531315A4D533936",
SYMLINK+="mypassport",
RUN+="rsync --recursive --times --perms --delete /home/avdzm/Pictures/* /media/$
#RUN+="echo ~/Sync!!!"


I cant figure out whats wrong....
I assume my symlink is incorrect n possibly the file name

any suggestions?

I'll appreciate any help

---

