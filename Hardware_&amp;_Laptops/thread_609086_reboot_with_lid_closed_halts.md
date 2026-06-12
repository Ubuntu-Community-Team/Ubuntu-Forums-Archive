---
title: "reboot with lid closed halts"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by rv8ch on 2007-11-10
I'm using a Dell Latitude CS 400 and 7.10 and when I do a```
 shutdown -r now
``` with the lid open, the system reboots fine.  If the lid is closed when I do this, the machine halts instead of rebooting.

I've got all power management turned off from the laptop's BIOS.  I see the same problem on two different identical laptops.

Anyone have any ideas how I can change this behavior?

Thanks,
Mickey

---

### Post by rv8ch on 2007-11-10
More investigation has proven that this has nothing to do with Linux, but is caused by what appears to be a "feature" of the Dell BIOS.  I've updated to the last BIOS available from them for this machine, and it shows the same problem.  Looks like I need to ensure that the lid does not get closed if I want to do a remote reboot of this machine.  I get the same problem even if I program the BIOS to start the machine at a particular time.  If it sees that the lid is closed, it just turns itself off.

Thanks,
Mickey

---

