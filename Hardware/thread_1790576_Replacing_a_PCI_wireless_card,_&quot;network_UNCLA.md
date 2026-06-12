---
title: "Replacing a PCI wireless card, &quot;network UNCLAIMED&quot;"
date: 2011-06-25
forum: Hardware
---

### Post by Arsic on 2011-06-25
I have this Asus 1015PEM and it came with a rt3090. Ran it straight through 10.04-11.04 releases, tested clean installs and upgrades. I decided to upgrade to the Intel Ultimate N WiFi Link 5300. Tried installing the drivers via Additional Drivers, but it doesn't detect anything new. Booted into Live CD/USB and it detected the card there, so that would mean there weren't any problems with the installation.

```
$ lspci | grep Wifi
02:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
$ sudo lshw -c net
  *-network UNCLAIMED     
       description: Network controller
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbffe000-fbffffff

```

Any help?

---

### Post by Arsic on 2011-06-25
Nevermind, I got it by downloading the driver from the Intel site and copied iwlwifi-5000-5.ucode to /lib/firmware.

> sudo rmmod -f iwlagn
sudo modprobe iwlagn

---

