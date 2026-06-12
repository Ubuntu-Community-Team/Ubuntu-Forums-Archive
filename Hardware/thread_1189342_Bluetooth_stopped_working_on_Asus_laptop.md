---
title: "Bluetooth stopped working on Asus laptop"
date: 2009-06-16
forum: Hardware
---

### Post by NdrU42 on 2009-06-16
Hi, I recently installed Ubuntu on my Asus M50 series laptop, but have problem with the bluetooth.

I wanted to connect my bt gps device to the computer, and after some searching  succeded (I could read the gps messages, but xgps showed no device).

But then, suddenly, the bluetooth stopped working. I thought a simple restart would do (I was a windows user for a long time), but it didn't.

The bluetooth adapter is connected, after enabling it (using hw button) dmesg shows:

```

[ 5911.530112] usb 5-1: new full speed USB device using uhci_hcd and address 6
[ 5911.703148] usb 5-1: configuration #1 chosen from 1 choice

```However, hciconfig says

```

ndru@ndru-laptop:~$ hciconfig 
hci0:    Type: USB
    BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:24 acl:0 sco:0 commands:8 errors:0

ndru@ndru-laptop:~$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)

```I found some mailing list where they suggested doing 

```

sudo /etc/init.d/bluetooth restart

```but that only adds INIT RUNNING after DOWN in hciconfig


The strangest thing is that it DID work, but then got broken somehow. I didn't change any files, i just used rfcomm to connect to the gps device.

---

