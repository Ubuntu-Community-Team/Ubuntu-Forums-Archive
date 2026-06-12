---
title: "Karmic, Virtualbox and USB devices"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by pmgeahan on 2009-11-03
Folks - 

Wanted to share an issue I ran into with Karmic and Virtualbox.

Under Jaunty, I had VirtualBox 3.0 installed with two Windows XP virtual machines and one Ubuntu VM.  All had USB working fine; I forget which tutorial I followed, but I created a vboxusers group, added myself to it, and put the following line in /etc/fstab:

```
none	/sys/bus/usb/drivers	usbfs	devgid=xxx,devmode=664	0	0
```

where 'xxx' is my vboxusers group ID.  

After upgrading to Karmic, I found that the USB devices in the VMs weren't working.  They appeared in the list, and I could select them, but the VMs wouldn't actually see them.  

Turns out two things had happened:  the first, that my user was no longer in /etc/group for vboxusers.  No idea why the upgrade would change that.

The second, and stranger, was that both XP VMs lost the drivers for the USB ports.  Both showed up with the question mark in the Control Panel.  Thankfully, fixing this was as simple as telling it to search Windows Update for the driver.  After that, everything was great.

Again, these two items were working perfectly before the upgrade; something in the upgrade changed them.  If you're having trouble with Virtualbox USB devices, it might be worth trying this.

---

