---
title: "X10 Firecracker via RS-232 Winchiphead Clone"
date: 2009-02-28
forum: Hardware
---

### Post by mastermindg on 2009-02-28
I'm running Ubuntu Hardy 64-bit on a Dell E-521. Unfortunately, it doesn't have any native serial ports, so I purchased an RS-232 (usbserial) cable to interface with my CM17A Firecracker. I've verified that the cable works with the device on windows (after installing the driver and the com port), so I know that the cable is not malfunctioning.

My problem is that when I run bottlerocket I am getting this error:

br: error: [Invalid argument] ioctl in br_cmd

I suspect this is related to the baudrate issues that I have read about; basically that the driver can only communicate at low baud and most devices will not work. I tried this post:

[http://ubuntuforums.org/showthread.php?t=921409](http://ubuntuforums.org/showthread.php?t=921409)

but only got this:

Good news! Module version  for ch341.ko
exactly matches what is already found in kernel 2.6.24-23-generic.
DKMS will not replace this module.


It seems that the module version is the same. I read about this patch here: [http://groups.google.com/group/linux.kernel/msg/1d6d57ebd0a25a23?dmode=source](http://groups.google.com/group/linux.kernel/msg/1d6d57ebd0a25a23?dmode=source)

and this seems to be the correct patch; however, I'm not comfortable with patching.

Has anybody else experienced similar problems and/or can assist me in getting this device to work correctly?

---

