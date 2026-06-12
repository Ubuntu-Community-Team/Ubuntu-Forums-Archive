---
title: "Installing on a Laptop with no CDROM"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by r8dhex on 2006-01-16
I want to install U5.10 on a laptop with no CDROM. What I did was take the laptop harddisk, plugged it into another computer using USB. 

Then using vmware, I setup a virtual machine using the USB laptop disk as a physical disk, then booted the virtual machine from the Ubuntu Install CD. I then installed onto the laptop harddisk (which appeared as /dev/sda).

It's now done up to the part where it needs to reboot. I'm planning to plug it back into the laptop, and boot it from there to continue the installation.

Obviously, the drive names are going to be different (/dev/sda will be /dev/hda on the laptop), and the hardware is also different.  So I'm not sure it will work.

I was wondering if anyone else has done something like this, or if anyone has a better way to install on a CDROM-less laptop, please tell me. 

Thanks

---

### Post by kaamos on 2006-01-16
Check this out: [https://wiki.ubuntu.com/Installation/FromUSBStick](https://wiki.ubuntu.com/Installation/FromUSBStick)
Also netinstall and other options are possible.

---

