---
title: "configuring touchscreen on hp pavilion tx 1301au"
date: 2008-05-22
forum: Hardware
---

### Post by aravamudan on 2008-05-22
Hi Guys !

I did the configuration for my hp laptop pavilion tx 1301au  (64  Turion amd )as per the archives posting by waspr. 

1. ServerLayout Section
InputDevice "EETI" "SendCoreEvents"

2.Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/usb/hiddev0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection

I replace "/dev/usb/hiddev0" because it crashed my X

Now when I do > sudo ./Touchkit
I get a message 

Please make sure the X module is installed and root permission is required to run this program.

and then displays a msg about egalax.

I have copied the .so file in the required path
cp egalax_drv.so /usr/lib64/xorg/modules/input/

when I do sudo cat /proc/bus/input/devices the egalax driver is loaded

P: Phys=usb-0000:00:0b.1.2.3/input0 

Am doing something wrong ?

Thanks in advance

---

### Post by aravamudan on 2008-05-23
Guys , 

Thanks anyway. It was an issue with the driver. Driver was throwing ABI version error.ignoreABI also wouldnt work. The new beta version available sorted the problem

Arav

---

