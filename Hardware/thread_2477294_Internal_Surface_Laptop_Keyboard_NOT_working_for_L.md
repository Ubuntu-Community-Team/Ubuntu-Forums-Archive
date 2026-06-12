---
title: "Internal Surface Laptop Keyboard NOT working for LUKS login"
date: 2022-07-20
forum: Hardware
---

### Post by anise-c on 2022-07-20
I recently replaced Windows OS on my Surface Laptop 3 with Ubuntu 22.04 LTS. I used LUKS encryption when performing the installation.
When I start up my Laptop the internal keyboard doesn't work for the LUKS password input screen. I have to connect an external keyboard to enter the password. The internal keyboard then works fine for all other uses.

I found a thread in [archlinux(dot)org]("https://bbs.archlinux.org/viewtopic.php?pid=1627263#p1627263") where someone had a similar problem albeit with a different type of Laptop. The solution they came to was to modify /etc/mkinitcpio.conf to include the missing keyboard related modules.

I have attempted to edit /etc/initramfs-tools/initramfs.conf to include surface specific modules I gleamed from the output of lsmod. This is what I have attempted thus far:
```
MODULES="usbhid hid_multitouch hid_generic surface_hid_core surface_hid surface_acpi_notify surface_battery surface_charger surface_platform_profile surface_aggregator_registry ipmi_devintf"
```
I also added systemd to a new line in the initramfs.conf file specifying HOOKS as the archlinux thread also suggested:
```
HOOKS="systemd base udev autodetect modconf keymap keyboard block encrypt lvm2 resume filesystems fsck"
```

But this hasn't resolved it. Assuming I'm on the right path I may be missing some more modules. Any help from the more experienced forum members would be greatly appreciated. Thanks.

__________________________________________________________

Found the solutions here:
[https://github.com/linux-surface/linux-surface](https://github.com/linux-surface/linux-surface)
[https://github.com/linux-surface/linux-surface/wiki/Disk-Encryption](https://github.com/linux-surface/linux-surface/wiki/Disk-Encryption)

---

