---
title: "USB Modem Device Name?"
date: 2012-11-26
forum: Hardware
---

### Post by PalapaGuy on 2012-11-26
I have a Sierra Wireless 250U USB modem and need to find out its device name.  I tried using command **lsusb **but it gave a device name that didn't appear to be correct.  Can someone tell me what I'm doing wrong?  Running 12.04 here.

---

### Post by dandnsmith on 2012-11-27
Why not post the name the command gave - sometimes devices give info which doesn't match what the device is sold as (manufacturing quirk)

---

### Post by varunendra on 2012-11-28
> **PalapaGuy said:**
> I have a Sierra Wireless 250U USB modem and need to find out its device name.  I tried using command **lsusb **but it gave a device name that didn't appear to be correct.  Can someone tell me what I'm doing wrong?  Running 12.04 here.
What matters is the Vendor & Product IDs [VID:PID] returned by lsusb, and it can not be wrong. It is directly read from the chip that has been used in the device, so would only differ if the manufacturer that you expect to see has only 'branded' the device, and didn't actually manufacture it.

By the way, what is your objective? If you need any technical assistance, please post the output of lsusb itself.


.

---

