---
title: "Hardy doesn't detect USB keyboard/mouse after resume from standby"
date: 2008-09-15
forum: Hardware
---

### Post by robobot on 2008-09-15
I'm having some issues with resuming from standby on Ubuntu Hardy.

When I resume from standby, my USB keyboard and mouse are not detected. However, when these are connected through PS-2, there is no problem. Unfortunately, I only have one PS-2 to USB adapter, so I need a different solution than this.

I have a Gigabyte GA-MA78GM-S2H motherboard, with the USB being handled by the AMD SB700 southbridge. I'm currently using S3 (suspend to RAM) standby.

---

### Post by phidia on 2008-09-15
You may need to take a look at /etc/default/acpi-support sometimes an edit or script is required there to bring usb back from suspend.
Edit: It looks like /etc/pm is now the place to create scripts for services that need to be stopped & re-started. Take a look at the thread [here]("http://ubuntuforums.org/showthread.php?p=5705728"), and hope that helps.

---

