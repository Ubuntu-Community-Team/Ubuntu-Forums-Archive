---
title: "USB Camera Connection Problem"
date: 2011-08-16
forum: Hardware
---

### Post by j2fraser on 2011-08-16
For some strange reason, my Canon Powershot SD800IS will no longer automount under Maverick (10.10) amd64, when connected by USB. It has worked flawlessly and reliably with Gthumb for months and months under this configuration. I recently installed a bunch of photo software (UfRaw, Raw Studio, Raw Therapee, Digikam, Darktable), so I'm concerned that the Borg may have come on board with one of these packages and mucked up HAL or something...

When I run dmesg, it seems to show the first part of a connection, but not any follow through:

> usb 1-7: new high speed USB device using ehci_hcd and address 7

But that's it.

When I run lsusb, I can see the camera... 

> Bus 001 Device 007: ID 04a9:3136 Canon, Inc. 


...but I try rebooting, replugging -- no response.

Does anybody have a clue where I should turn from here, as far as troubleshooting is concerned?

---

### Post by j2fraser on 2011-08-16
I should have also mentioned that when I run: ```
sudo fdisk -l
``` I do not see the camera.

---

### Post by j2fraser on 2011-08-18
bump

---

### Post by j2fraser on 2011-08-23
bump

---

