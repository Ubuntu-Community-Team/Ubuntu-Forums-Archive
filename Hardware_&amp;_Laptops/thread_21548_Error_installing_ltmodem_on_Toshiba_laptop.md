---
title: "Error installing ltmodem on Toshiba laptop"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by eroteme on 2005-03-22
Hi, I have been trying to install the ltmodem module into Ubuntu using the following guide: [http://ubuntuforums.org/showthread.php?t=6361](http://ubuntuforums.org/showthread.php?t=6361)

The laptop - a Toshiba 3480CT - has a Lucent MARS modem that should, AFAIK be supported.

I managed to compile the driver and install the kernel module but rebooting there are a number of fatal errors and X refuses to start. I assume that the ltmodem module is causing problems and that this in turn has halted other vital modules that stop X from running.

Is there a simple way to uninstall the module from the kernel? Running lsmod, ltmodem doesn't even appear so I'm completely lost.

Going through the log files one relevant message reads:
"No module symbols loaded - kernel modules not enabled"

Any advice would be greatly appreciated. Further info from logs can be provided if someone can explain how to get that information...

Thanks.

---

