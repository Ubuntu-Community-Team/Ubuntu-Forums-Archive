---
title: "How to Disable a specific device?"
date: 2009-02-27
forum: Hardware
---

### Post by sniperbob on 2009-02-27
Hi - I am hoping there is a quick / obvious answer for this that I was unable to find in my google & forum searches:

I am looking to disable a device on my system, specifically uhci_hcd:usb4.

I dont want to kill ALL usb, just usb4. It is consistently causing interrupt conflicts with eth0. They are both onboard, and the BIOS gives me no options to tweak IRQ's, or enable/disable individual USB controllers.

After the system has been up for more than a few hours, the box's ethernet link stops responding. checking dmesg, I get one of those "nobody cared" errors, and the kernel kills the IRQ (which has usb4 and eth0 on it).

Anyway - I was hoping there was something I could do, a rule in udev or something - to just not load, or forcibly kill if I have to, the device for usb4. I have no devices connected to it and just want it to stop killing my eth0.

---

