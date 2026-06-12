---
title: "access denied to parallel port when setting up hpoj"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by garba on 2005-05-27
Good day, I hope somebody can help me out because this is driving me insane... looks like I cant get hpoj (that's the driver provided by hp for their laserjet printers line of products) to probe my parallel port, syslog reports "access denied to parallel port"... tried googling it but no human being other than me seems to be having the same problem ^^ any idea? tia

---

### Post by rocteur on 2005-06-05
I have exactly the same problem.

This compuer as running SUSE and all this worked so I don't think it is a hardware or bios problem.

Jun  5 19:59:19 localhost ptal-mlcd: FATAL ERROR at ParPort.cpp:48, dev=<mlc:par:probe>, pid=9541, e=1, t=1117994359         Access 
denied to parallel port!

---

### Post by rocteur on 2005-06-05
Reading this:

[http://ubuntuforums.org/showthread.php?t=15142&highlight=hpoj+access+denied](http://ubuntuforums.org/showthread.php?t=15142&highlight=hpoj+access+denied)

I removed hpoj and installed the hoary version and the same problem:

I've also found this in the log files:

Jun  5 21:24:40 localhost ptal-mlcd: ERROR at ExMgr.cpp:2525, dev=<mlc:usb:probe>, pid=11106, e=11, t=1117999480         Couldn't find device!

Also this in the debug log file:

Jun  5 21:21:08 localhost kernel: FIFO write timed out
Jun  5 21:22:18 localhost kernel: parport0: FIFO is stuck
Jun  5 21:22:28 localhost kernel: FIFO write timed out
Jun  5 21:23:38 localhost kernel: parport0: FIFO is stuck
Jun  5 21:23:48 localhost kernel: FIFO write timed out

---

