---
title: "Unable to suspend the laptop"
date: 2010-06-02
forum: Hardware
---

### Post by Zoxel on 2010-06-02
Ubuntu 10.04 x86_64, all latest system updates installed.
When I close the lid or execute the following command:```
zox@ZNETBOOK:~$ sudo pm-suspend
```My laptop will not suspend - it tries but fails.
I get the following errors in the **dmesg** log:```
[ 2975.752823] PM: Syncing filesystems ... done.
[ 2976.182577] PM: Preparing system for mem sleep
[ 2976.182583] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2976.183954] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2976.184062] PM: Entering mem sleep
[ 2976.184077] Suspending console(s) (use no_console_suspend to debug)
[ 2976.200164] ohci_hcd 0000:05:00.1: PCI INT B disabled
[ 2976.250072] ohci_hcd 0000:05:00.0: PCI INT A disabled
[ 2976.270090] sd 3:0:0:0: [sda] Synchronizing SCSI cache
[ 2976.270328] sd 3:0:0:0: [sda] Stopping disk
[ 2976.776715] PM: suspend of drv:sd dev:3:0:0:0 complete after 506.624 msecs
[ 2977.177979] PM: suspend of drv:psmouse dev:serio4 complete after 367.901 msecs
[ 2977.270263] pm_op(): usb_dev_suspend+0x0/0x20 returns -16
[ 2977.270266] PM: Device usb1 failed to suspend: error -16
[ 2977.270268] PM: Some devices failed to suspend
[ 2977.400090] PM: resume of drv:usb dev:usb2 complete after 129.755 msecs
[ 2977.519535] sd 3:0:0:0: [sda] Starting disk
[ 2978.582179] PM: resume of drv:sd dev:3:0:0:0 complete after 1062.642 msecs
[ 2978.644156] input input6: event field not found
[ 2978.648195] ohci_hcd 0000:05:00.0: PCI INT A -> Link[LNK4] -> GSI 11 (level, low) -> IRQ 11
[ 2978.860069] PM: resume of drv:usb dev:usb3 complete after 109.997 msecs
[ 2978.860091] ohci_hcd 0000:05:00.1: PCI INT B -> Link[LNK4] -> GSI 11 (level, low) -> IRQ 11
[ 2978.954174] PM: resume of devices complete after 1683.901 msecs
[ 2978.954359] PM: resume devices took 1.680 seconds
[ 2978.954378] PM: Finishing wakeup.
[ 2978.954379] Restarting tasks ... done.
```The **lsusb** command shows the following:```
zox@ZNETBOOK:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:0065 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 002: ID 0d49:7350 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```What command can I use to forcibly disable usb subsystem during suspend:confused:

BTW: The **pm-hibernate** works perfectly.

---

### Post by Zoxel on 2010-06-18
Last package update resolved the issue and the following bug was closed:

[https://bugs.launchpad.net/bugs/589594](https://bugs.launchpad.net/bugs/589594)

---

### Post by dino99 on 2010-06-18
so mark this post as SOLVED (thread tools)

---

