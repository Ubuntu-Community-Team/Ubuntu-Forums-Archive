---
title: "USB 3.0 PCIE expansion card not recognized on Ubuntu (DL380 G8"
date: 2021-07-04
forum: Hardware
---

### Post by randhomejoe on 2021-07-04
Hello there,

I am fairly new to Linux.

I have installed USB 3.0 PCIE expansion card [https://www.pdf-manuals.com/hp-4-port-usb-3-0-superspeed-pcie-1x-card-qt587aa-295698-manual](https://www.pdf-manuals.com/hp-4-port-usb-3-0-superspeed-pcie-1x-card-qt587aa-295698-manual) on my DL 380 G8 running on DL380 G8 but it is not recognized.

The card gets the power from the optical drive slim line connected to the sata power.

The pluged in USB does flash (so it gets the power) but is not recognized in Ubuntu.

Can somebody please help?

Do I need to install additional drivers or what is the issue here?

---

### Post by mastablasta on 2021-07-07
what linux distro are you using? Ubuntu Server? or are you using a  desktop OS? also which version 20.04?

command:

```
lspci
```

will show all PCI connected devices and cards.

command:
```
lsusb 

```
will list all USB devices plugged "directly" into the motherboard or via PCI card.

if it get's recognised by these commands, then it might need a kernel parameter, to force it to work. 

if it doesn't get recognised, then you need a newer kernel or you need to patch the kernel with drivers.

the commands might also reveal the actual chip, so we can see if it needs additional driver or if driver is already in kernel.

other things to try (some people reported these to work for some unknown reason):
if there are other PCIe slots, try moving it
try turning off legacy boot
Try kernel parameter: pci=nocrs  - how to use kernel parameters: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
check dmesg log with nano (if this is server) or logviewer (if this is deskotp)

---

