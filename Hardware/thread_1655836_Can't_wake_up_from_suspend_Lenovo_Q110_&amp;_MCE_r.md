---
title: "Can't wake up from suspend: Lenovo Q110 &amp; MCE remote"
date: 2010-12-30
forum: Hardware
---

### Post by garsh on 2010-12-30
I have a [Lenovo Q110]("http://computershopper.com/desktops/reviews/lenovo-ideacentre-q110") running Ubuntu 10.10 64-bit as a MythTV frontend.  It works great in this role, but I'd like to be able to make it suspend & wake up using the remote.

I'm using a USB-attached Windows MCE receiver & remote.  When I run Windows 7 on this machine, I can suspend it, and then pressing the PC button on the remote will wake it back up.  I see the red LED on the receiver light up when I press the PC button.  But when running Mythbuntu, the remote will not wake it up.  In this case, I do not see the red LED on the receiver.  This is the LED that usually lights up whenever the receiver detects an infrared signal.

I've examined /proc/acpi/wakeup.  I've tried enabling each of the USB devices listed in there individually, as well as all at once.  I've even tried enabling *every* device in that list, but I still can't get the computer to wake up via the remote.  The USB keyboard that I have attached *does* wake up the computer when I enable USB0.

So, I'm stumped.  Any suggestions?

My current /proc/acpi/wakeup:
```
garsh@mythtv:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
SMB0      S4    *disabled  pci:0000:00:03.2
NMAC      S5    *disabled  pci:0000:00:0a.0
PBB0      S4    *disabled  pci:0000:00:09.0
HDAC      S4    *disabled  pci:0000:00:08.0
XVR0      S4    *disabled
XVR1      S4    *disabled
P0P5      S4    *disabled
P0P6      S4    *disabled
P0P7      S4    *disabled
P0P8      S4    *disabled
P0P9      S4    *disabled
USB0      S3    *enabled   pci:0000:00:04.0
USB2      S3    *enabled   pci:0000:00:04.1
US15      S3    *enabled   pci:0000:00:06.0
US12      S3    *enabled   pci:0000:00:06.1
PWRB      S4    *enabled

```

---

### Post by garsh on 2010-12-30
Found the answer.  There's some file specific to the device plugged into a USB port that also needs to be enabled to allow wakeup.  The following little snipped of code will set this file appropriately.
```
#!/bin/sh
mce_id="0815" # The id for the MCE receiver.
for i in /sys/bus/usb/devices/?-?/idProduct
do
        id=`cat $i`
        if [ $id = $mce_id ]
        then
                wakeup=`echo $i | sed 's/idProduct/power\/wakeup/'`
                echo enabled > $wakeup
        fi
done

```

---

### Post by slcpunk on 2011-08-19
2 thumbs up!! 

One day my keyboard stopped waking up my computer for no aparent reason.  I also tried all the /proc/acpi things with no luck.

I had resorted to using my power button until today! 

thanks so much.

For others, if you don't know how to get the ID of your device, just do "lsusb" from the command line, you are looking for the second half of the ID( after the colon ) shown here:

Bus 007 Device 008: ID 045e:00dd Microsoft Corp.

IE: 00dd

---

