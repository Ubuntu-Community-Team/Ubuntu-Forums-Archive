---
title: "Trying to make Karmic talk to my phone"
date: 2010-03-14
forum: Hardware
---

### Post by woodmaster on 2010-03-14
Hi all,
     I have a Samsung Alias2 and am trying to get to be able to transfer mp3's to it.  I'm trying to configure Wammu(Gammu) for it, but it gives me the following error when I direct it to the USB port the phone is plugged into:
```
Failed to connect to phone

Description:error during reading from the device
Function:init
Error code:12
```

I do have the necessary permission cause I opened myself up to all USB devices via:
[http://tuxpool.blogspot.com/2009/12/changing-usb-device-permissions-in.html]("http://http://tuxpool.blogspot.com/2009/12/changing-usb-device-permissions-in.html")

I'm pretty sure I have the right USB port cause lsusb gives
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04e8:6640 Samsung Electronics Co., Ltd Usb Modem Enumerator
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a9:1718 Canon, Inc. MP600 Storage
Bus 001 Device 002: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
which tells me that /dev/bus/usb/004/002 is my mount point for the phone.  Any other advice on what I could try?

---

