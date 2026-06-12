---
title: "usb 2.0 &amp; usb 3 port is not working in ubuntu 14.04 LTS"
date: 2015-08-21
forum: Hardware
---

### Post by swopnil on 2015-08-21
Hi, 
I am new user in ubuntu. I install ubuntu 14.04 LTS in my laptop. My Laptop configuration is HP Probook 450 G1. I install ubuntu usb flash drive. After install is not working usb 2 & usb 3 port. How i solve this problem ? Please help me...........

---

### Post by dino99 on 2015-08-21
when something goes wrong, then you might think tp glance to the logs (into /var/log/ , mainly dmesg ; and into your Home : .xsession-errors (ctrl+h to unhide it) ) for finding warnings/errors that can help fixing the issues.

but from a terminal, run these commands first to update the hardware ids:
> sudo update-pciids
sudo update-usbids

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a 
indeed the bios settings matters also; check you already have the latest bios installed for this lappy model

---

### Post by oldfred on 2015-08-21
Similar model, some of issues discussed. Did not see anything specific to USB ports, but many other settings should be changed in UEFI.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"

[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)

---

