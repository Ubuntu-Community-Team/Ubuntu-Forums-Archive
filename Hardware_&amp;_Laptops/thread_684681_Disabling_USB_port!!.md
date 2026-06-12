---
title: "Disabling USB port!!"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by delwestcott on 2008-02-01
Laptop: MIC 2.4Ghz
OS: UBUNTU Linux 7.10

have tried disabling the USB ports (3 of them) in the BIOS and don't see any intuitive options available for disabling the ports.  If it exists please tell me the menu the option is under, and the name of the option.

Alternative method...found 2 USB 1.0 Controllers in the device manager but I am unfamiliar with Linux...how do I go about disabling these in the device manager???  please help.  thnx!

---

### Post by myforefront on 2008-02-08
if you want to disable usb for some thumb drive or external HDD,..

You might disable the auto mount service,..

In Freespire its call Jiffymount,... (just remove the permission "chmod a-rwx" all jiffy* files)

I'm not quite sure in ubuntu,.. you can check by looking at message file in /var/log/messages using tail -f [file name].

Watch what will show if you plug a usb thumbdrive.

Then try to remove the permission of that file..

Hope it will help,...

---

