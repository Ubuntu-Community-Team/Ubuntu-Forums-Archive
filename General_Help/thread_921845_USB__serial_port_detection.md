---
title: "USB / serial port detection"
date: 2008-09-16
forum: General Help
---

### Post by dingfelder on 2008-09-16
I am using multiple USB FTDI serial port devices.

When I plug them in, they are correctly detected and work properly, if I can guess what port they are on, such as /dev/ttyUSB0

If I plug 3 devices in, they might get mapped as:

/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2

if I then unplug the one connected to /dev/ttyUSB1, I expect to see 

/dev/ttyUSB0
/dev/ttyUSB3

but frequently Ubuntu does not release /dev/ttyUSB1

if I then plug it in again, I see

/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2
/dev/ttyUSB3

or some times wacky stuff like

/dev/ttyUSB1
/dev/ttyUSB2
/dev/ttyUSB4

It is safe to say that I prefer Ubuntu over Windows for most things.  USB detection is not one of them though.  For me, in Windows, the os ALWAYS maps the same physical FTDI device to the same com port.  

For example, in windows: 

[LIST=1]I plug in 3 devices today, and they map as com1, com2, and com3[/LIST]
[LIST=2]I identify which physical device is using which port, and mark the com port names on each device.[/LIST]
[LIST=3]If I then plug in the device that was marked com3 in tomorrow, the device will still get set to com3 even if com1 and com2 are not being used.[/LIST]

in ubuntu: 

[LIST=1]if the usb detection works correctly (which it frequently seems not to) all the devices go away if I unplug all the usb connections.[/LIST]
[LIST=2]assuming ls /dev/ttyUSB* shows nothing, if I plug in the device that used to be mapped to /dev/ttyUSB2, this time it will get mapped to /dev/ttyUSB0[/LIST]


No matter what else happens, if I unplug a usb port, that /dev/USBx link really need to go away.  Other behaviors may be nice to haves but this one is a bug IMHO

I prefer that the os should remap devices to the same port they used last time, if it is available.  If it is not available, it starts with 0

Does anyone have any suggestions for making port mapping and port detection work better?  Or is there a tool or hack to do this automagically?

---

### Post by dingfelder on 2008-09-16
Investigating a bit more, it seem that some manual work can be done with udev to force the ports to always get a particular name, based upon their device serial number

I created a local udev file: 
touch /etc/udev/rules.d/10-local.rules
sudo chmod 644 /etc/udev/rules.d/10-local.rules

edit it and add:

BUS=="usb", SYSFS{idProduct}=="6001", SYSFS{idVendor}=="0403", SYSFS{serial}=="FTCVO0CQ", NAME="FTDI_devicename1"
BUS=="usb", SYSFS{idProduct}=="6001", SYSFS{idVendor}=="0403", SYSFS{serial}=="FTCVNYPN", NAME="FTDI_devicename2"
BUS=="usb", SYSFS{idProduct}=="6001", SYSFS{idVendor}=="0403", SYSFS{serial}=="FTCVNZZE", NAME="FTDI_devicename3"

After doing that, when I plug my cables in, I always get /dev/FTDI_devicename3 etc irregardless of how the normal internal mapping is done.

you have to get the idProduct, idVendor & serial number from udevinfo

See the following articles for details on doing that.

[http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/)

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

Having said that, I still think there is a bug where sometimes usb ports dont get freed up and I think some of this mapping should be done automatically instead of requiring me to go through all these hoops.

---

### Post by notslate on 2009-02-10
Raising an older (but helpful) thread.  I am connecting multiple usb-to-serial converter cables also.  This solution doesn't work for me because there is no serial number returned by udevinfo.

In fact, when I try multiple cables (all of the same mfg), udevinfo doesn't show any different info that can be used in the rules to force the mapping.

Does anyone have an example of a cable that works for them and provides a serial number that can be used to create the rule?  If so, all I want is mfg and p/n and I'll get those cables...unless someone has an idea to get serial number info from these cables that I can try out.

Thanks!

---

### Post by dingfelder on 2009-02-10
I can not easily provide the exact model, but the manufacturer is FTDI

Cheers,

Ding

---

### Post by notslate on 2009-02-10
Nice, thanks for the response.  Is this the one?  

[http://apple.clickandbuild.com/cnb/shop/ftdichip?productID=56&op=catalogue-product_info-null&prodCategoryID=45](http://apple.clickandbuild.com/cnb/shop/ftdichip?productID=56&op=catalogue-product_info-null&prodCategoryID=45)

Although mine have labels, there is no manufacturer name, lsusb shows this:

ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

I have a bunch of them but I can't get them to work for me.

---

### Post by dingfelder on 2009-02-10
that does look like the beast.

I got one of our propeller heads to get me the info for it, it will be something like:

```

T:  Bus=01 Lev=02 Prnt=55 Port=01 Cnt=02 Dev#= 61 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0403 ProdID=6001 Rev= 6.00
S:  Manufacturer=FTDI
S:  Product=US232R
S:  SerialNumber=FTDVQ1HD
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=ftdi_sio
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

this is from:
/proc/bus/usb
Just "cat"ting the file "devices"

---

