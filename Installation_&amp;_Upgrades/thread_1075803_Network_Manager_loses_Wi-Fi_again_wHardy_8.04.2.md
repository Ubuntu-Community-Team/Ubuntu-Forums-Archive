---
title: "Network Manager loses Wi-Fi again w/Hardy 8.04.2"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by TimDaniels on 2009-02-20
Under Hardy 8.04.1, with old Broadcom driver, diddling with Network Manager permanently turned off Wi-Fi for Ubuntu.  The Bluetooth mouse continued to run fine, and in the dual-booted Vista both Wi-Fi and Bluetooth worked fine.

I finally re-installed Ubuntu, going with version 8.04.2 that had the STA Broadcom driver, and I selected that driver from the two listed in Hardware Devices.  Bluetooth worked fine, but although Wireless Networking was available as an option and checked as an option, Ubuntu wouldn't connect to my wireless router although it could see the wireless router.  I diddled, finally unchecking the Roaming option in Network Manager.  And that removed Wi-Fi as an option in Network Manager, and the Bluetooth mouse couldn't be seen.  In the dual-booted Vista, Wi-Fi still works fine, but the Bluetooth mouse isn't seen.

It appears that something in the Broadcom wireless driver for Ubuntu has turned off Wi-Fi in Ubuntu and Bluetooth for both Ubuntu and Vista.  Does anyone know of a solution for this?  I'm getting really annoyed.

*TimDaniels*

---

### Post by TimDaniels on 2009-02-20
> **TimDaniels said:**
> 
I finally re-installed Ubuntu, going with version 8.04.2 that had the STA Broadcom driver, and I selected that driver from the two listed in Hardware Devices.  Bluetooth worked fine, but although Wireless Networking was available as an option and checked as an option, Ubuntu wouldn't connect to my wireless router although it could see the wireless router.  I diddled, finally unchecking the Roaming option in Network Manager.  And that removed Wi-Fi as an option in Network Manager, and the Bluetooth mouse couldn't be seen.  In the dual-booted Vista, Wi-Fi still works fine, but the Bluetooth mouse isn't seen.


Progress.  I had the command to pair the mouse with the laptop wrong.  I was trying to use `hdd` instead of `hidd`.  With the latter, I was able to get the Bluetooth mouse working in Ubuntu and now it works in Vista as well.  And in Vista, Wi-Fi is now working fine, too.

But Wi-Fi in Ubuntu continues not to work, with there being no Wireless Networking as an option in Network Manager.

*TimDaniels*

---

