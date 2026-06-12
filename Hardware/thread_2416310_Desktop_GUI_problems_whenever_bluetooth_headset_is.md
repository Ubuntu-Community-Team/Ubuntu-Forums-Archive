---
title: "Desktop GUI problems whenever bluetooth headset is connected"
date: 2019-04-08
forum: Hardware
---

### Post by bjorn1232 on 2019-04-08
Hello,
I've had quite a headache trying to figure out what the cause is to some seemingly random problems with my Ubuntu 16.04. These problems involve windows becoming unresponsive, the scroll wheel deactivating and certain keyboard commands becoming unusable. I have reinstalled and installed Ubuntu several times until I realized that the problems only arise when my wireless headphone adapter is plugged in to a USB port (no matter which one). I have plenty of USB devices that works perfectly fine, but as soon as I plug in this particular adapter, all these GUI/desktop/window-related problems arise. These problems does not occur with Windows, Mac or Ubuntu 18.04.
How do I troubleshoot this? How can a bluetooth headphone adapter cause the entire desktop enviroment to essentially break?

The headphones are the *Corsair HS70 Wireless.*
When the Bluetooth adapter is plugged in, it appears as
```
Bus 003 Device 003: ID 1b1c:0a38 Corsair
```
when *lsusb* is called.

Here is a paste from my systemlog when inserting the adapter and then removing it 20 seconds later:
[https://pastebin.com/raw/JtquUBCf](https://pastebin.com/raw/JtquUBCf)

Please help. Thank you.

---

