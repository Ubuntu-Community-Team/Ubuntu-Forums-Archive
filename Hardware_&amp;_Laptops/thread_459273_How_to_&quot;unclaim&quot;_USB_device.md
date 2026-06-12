---
title: "How to &quot;unclaim&quot; USB device?"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2007-05-30
My configuration is as follows:
[LIST=1]
[*]Ubuntu 6.06
[*]VMware 5.5.4 build-44386
[*]Windows XP SP2 running as a virtual machine inside VMWare.
[*]ISSC Bluetooth USB dongle
[/LIST]

It works - inside the Windows XP VM - but whenever I unplug and re-plug the USB dongle (or reboot the XP virtual machine), I get after a **very long delay** (minutes) the following message:

> The specified device appears to be claimed by another driver (hci_usb) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver.

Once I confirm this message box (press OK), all is well. However, this is very annoying since it significantly impacts my productivity (I need to reboot and plug/unplug frequently for a project I am working on).

As I understand it, this stems from VMWare attempting to grab the device (hci_usb) from Linux. I believe that if I tell Linux in some way to disown/release the device, those delays will be eliminated.

Is there a way to tell Linux to **NOT CLAIM** hci_usb?

(without jeopardizing VMWare's chance of recognizing that the USB device is in, that is.)

If so, how do I do that?

Thanks!
Alex 

P.S. This ISSC (Integrated System Solution Corp.) dongle is identified in the User's Manual as "BT Dongle-IS1002N Horus Module". In the Windows BlueSoleil software it is identified as IVT. In Ubuntu's Device Manager it is identified as [KY-BT100 Bluetooth Adapter]("http://www.qbik.ch/usb/devices/showdev.php?id=3915").

---

