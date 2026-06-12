---
title: "[SOLVED] gpsd and USB path (garmin)"
date: 2008-07-17
forum: Hardware
---

### Post by ds6 on 2008-07-17
Good day, 

I am have trouble determining the path to my USB gps device. To start gpsd I must specify a device name and path.

This is the out put from lsusb:

Bus 003 Device 002: ID 091e:0003 Garmin International GPSmap (various models)

I have also tried "lshw" and "mount". 

The gpsd command should look something like: 
gpsd -nN /dev/ttyUSBx 

How can I determine /dev/xxxxx for a USB device?
or How can I create that device?

Thank you for your help. 
I did search the forum and googled for an answer....nothing overly helpful.

---

### Post by ds6 on 2008-07-17
Found the fix on anther post...


$sudo modprobe garmin_gps
sudo ln -sb /dev/ttyUSB0 /dev/ttyS3 .......(to map the USB port to COM4,)

---

### Post by nixi on 2009-01-16
Wish you could share a link to that other post... I can't get gpsd to start.

---

### Post by TheMrOrange on 2009-05-21
I'm using GPS60 garmin
I tried but gpsd doesn't receive:
# modprobe garmin_gps
# ln -sb /dev/ttyUSB0 /dev/ttyS3

# gpsd -N -D 6 /dev/ttyUSB0 
gpsd: launching (Version 2.38)
gpsd: listening on port gpsd
gpsd: Priority sertting failed.
gpsd: shmat(458764,0,0) succeeded
gpsd: shmat(491533,0,0) succeeded
gpsd: shmat(524302,0,0) succeeded
gpsd: shmat(557071,0,0) succeeded
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: speed 9600, 8N1
gpsd: => GPS: $PASHQ,RID*28\x0d

gpsd: Navcom: command dump: 0299661c0800040200001203
gpsd: => GPS: 0299661c0800040200001203
gpsd: Navcom: sent command 0x1c (Test Support Block)
gpsd: Navcom: command 0x1c mode = 02, length = 0
gpsd: Navcom: command dump: 029966200e000001ae02000071000000f203
gpsd: => GPS: 029966200e000001ae02000071000000f203
gpsd: Navcom: sent command 0x20 (Data Request) - data block id = ae at rate 00
gpsd: Navcom: command dump: 029966200e00000186020a0071000000d003
gpsd: => GPS: 029966200e00000186020a0071000000d003
gpsd: Navcom: sent command 0x20 (Data Request) - data block id = 86 at rate 0a
gpsd: Can't open /proc/bus/usb/devices
gpsd: no probe matched...
gpsd: gpsd_activate(1): opened GPS (5)


after that i must kill the process to exit because it's frozen 

suggestion? link?

---

### Post by SniperSlap on 2009-08-31
> **ds6 said:**
> Found the fix on anther post...


$sudo modprobe garmin_gps
sudo ln -sb /dev/ttyUSB0 /dev/ttyS3 .......(to map the USB port to COM4,)

Is this needed for USB garmins?

---

