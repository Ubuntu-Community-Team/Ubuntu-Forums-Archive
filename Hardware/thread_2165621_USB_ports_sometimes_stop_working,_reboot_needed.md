---
title: "USB ports sometimes stop working, reboot needed"
date: 2013-08-05
forum: Hardware
---

### Post by amarumayo on 2013-08-05
Hi all,

Occasionally my USB ports will not recognize any device that I have plugged in to them.  The only way I can remedy the problem is to do a reboot.  Anyone have any ideas what may be causing this or how I can go about troubleshooting the problem?

Thanks in advance,
Chris

---

### Post by bapoumba on 2013-08-05
Does it always happen with the same device or is it random ?
What does **lsusb** outputs ?
I will be off shortly (night here) but others will help you :)

---

### Post by amarumayo on 2013-08-05
It appears to be random. **lsusb outputs:**

lsusb
Bus 001 Device 002: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. Card reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by bapoumba on 2013-08-06
I'm not on my ubuntu box so I cannot check if these are still valid :
[https://help.ubuntu.com/community/DebuggingUSBStorage](https://help.ubuntu.com/community/DebuggingUSBStorage)
[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

I'll be moving this thread to the Hardware forum so that others may be able to help you troubleshoot your setup.
Edit : moved.

---

### Post by VMC on 2013-08-06
I'm very attentive to USB error messages. There's a problem right now with the current kernels.

Here's something to try. open a terminal and type the following:
```
tail -f /var/log/syslog
```Then plug in your USB device and observe the outputs. If it doesn't mount right away, give it time-around 6 minutes.
Then bring back the results.

---

