---
title: "suspend issue: pm_op(): usb_dev_suspend+0x0/0x10 returns -2"
date: 2010-02-22
forum: Hardware
---

### Post by akos.maroy on 2010-02-22
I'm trying to suspend or hibernate my laptop. I'm following this guide: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) to collect information. neither suspend nor hibernate works - and this is what I get in dmesg:

```
[  685.833275] PM: Entering mem sleep
[  685.833292] Suspending console(s) (use no_console_suspend to debug)
[  685.993399] pm_op(): usb_dev_suspend+0x0/0x10 returns -2
[  685.993404] PM: Device usb2 failed to suspend: error -2
[  685.993408] PM: Some devices failed to suspend
[  685.997009] PM: resume devices took 0.000 seconds
[  685.997169] PM: Finishing wakeup.

```

this happemns on a 2.6.32.8 kernel, but also the same with 2.6.33-rc8. I have the following USB devices:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 04f2:b16c Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I wonder if "Device usb2" means "Bus 001 Device 002: ID 8087:0020" from the above list. with a little bit of google'ing, this seems to be:

```
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
```

for example from here: [http://forum.notebookreview.com/showthread.php?p=5906076](http://forum.notebookreview.com/showthread.php?p=5906076)

is there a way to find out more about this device? or just black list it somehow?

---

