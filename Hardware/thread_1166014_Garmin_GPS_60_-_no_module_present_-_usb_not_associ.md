---
title: "Garmin GPS 60 - no module present - usb not associated"
date: 2009-05-21
forum: Hardware
---

### Post by TheMrOrange on 2009-05-21
Hi,
I'm trying to use my Garmin GPS60 USB using Ubuntu. I would like to capture real time date using gpsd.
I'm using Dell LatitudeI and I tried Ubuntu 8.10 and 9.04 but the problem is the same in both versions:

After Garmin plug in
# dmsg
[ 2134.840143] usb 2-1: new full speed USB device using uhci_hcd and  address 4
[ 2135.481231] usb 2-1: configuration #1 chosen from 1 choice

# lsusb
Bus 002 Device 005: ID 091e:0003 Garmin International GPSmap (various models)





from gpsd-user-list somebody (who is using Garmin GPS60csx) send me his lsmod and dmesg log.
lsmod shows the following two modules:
garmin_gps             14488  0
usbserial              24264  1 garmin_gps

dmesg shows:
May 21 05:58:37 comp usb 2-2: new full speed USB device using uhci_hcd and address 2
May 21 05:58:37 comp usb 2-2: configuration #1 chosen from 1 choice
May 21 05:58:37 comp garmin_gps 2-2:1.0: Garmin GPS usb/tty converter detected
May 21 05:58:37 comp usb 2-2: Garmin GPS usb/tty converter now attached to ttyUSB0



my lsmod doesn't show anything similar modules!
and in my dmesg doesn't appear following last two lines: 
May 21 05:58:37 comp garmin_gps 2-2:1.0: Garmin GPS usb/tty converter detected
May 21 05:58:37 comp usb 2-2: Garmin GPS usb/tty converter now attached to ttyUSB0

How I can fix it?
Should I reinstall garmin_gps driver? which version? 

help please

---

### Post by taing on 2009-08-15
Try to comment out the line

[FONT=Verdana, Arial, Helvetica][SIZE=2][COLOR=midnightblue]blacklist garmin_gps

from the file [/COLOR][/SIZE][/FONT][FONT=Verdana, Arial, Helvetica][SIZE=2][COLOR=midnightblue][FONT=courier][SIZE=2]/etc/modprobe.d/blacklist

found this on [http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878](http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878)

[/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

