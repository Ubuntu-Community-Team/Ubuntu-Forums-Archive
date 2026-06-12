---
title: "Dapper on Dell install issues"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by cltrenholm on 2006-10-10
Hello,

I have a Dell Power Edge 2950 with a PERC5/I RAID controller, RAID 1 mirrored 36 Gb SAS drives and a Broadcom NetXtreme NIC.

The install does not detect the NIC but I suspect I can reconfigure after the fact to get them up and running.

The install appears to go fine and the RAID partition and controller are detected however when the system attempts to reboot at the end of the installation it hangs. I do a cold shutdown, power up and the system begins to load however I get the following message:

/dev/sda1 does not exist. Dropping to a shell

Busybox 1.01 Debian 1:1.01-4ubuntu3 Built in shell (ash)

/bin/sh can't access tty control job ending

It would appear that the RAID partition is not accessible after the install however it does get detected during the install.

Can anyone provide guidance on either of the two issues above; preferably the controller issue?

Chris

---

### Post by rcgabriel on 2006-10-27
See [this thread]("http://ubuntuforums.org/showthread.php?t=226114") for useful advice, if you haven't seen it already.  I followed the instructions on the third page exactly, and have everything working just fine now with a PERC RAID-1 array.  The gist is that GRUB screws up a bit and uses sda, the physical drive, instead of sdc, the logical RAID drive, and you have to change a couple settings after install but before you reboot.

I have 2 of the Intel dual-port ethernet cards I'm using and eth0 through eth3 work great with no tweaks for me.  Some people had to make a few config file tweaks to get the built-in ethernet working properly, apparently.

---

