---
title: "usb drive stopped working (system ignoring it completly)"
date: 2015-08-10
forum: Hardware
---

### Post by AllesMeins on 2015-08-10
Since this morning one of my two usb drives stopped working with my system. It just doesn't show up anywhere. When plugging it in, the drive spins up and the status led shows that it is ready, but my system does not react in any way - there are no mesages in "dmesg", it is not listed in "lsusb" and doesn't show up under fdisk -l. The strange thing is: the same drive works fine with my laptop (running lubuntu as well). I've tried switching ports (no change in behaviour) and I've tested a different usb-drive which works fine. So I'm pretty lost: What could be a reason for Linux to completly ignore this one drive? And how can I fix it?

---

### Post by dino99 on 2015-08-11
maybe try:
> sudo update-pciids
sudo update-usbids

it should be good to know if the bios find that device, and if gparted complaint about its partition(s). Also can you tell about the version used please, and how that device is formatted.
gparted-live can help rebuilding the partition(s) table (safed data)

---

### Post by AllesMeins on 2015-08-11
Hi,

thanks for your reply... I just noticed, that the problem somehow "magically" fixed itself. I let the system run over night (for some other reasons) and in the morning my drive was there again. It seems it only took Lubuntu (14.04) just really long (at least one hour) to recognize it. I'm going to wait and see if that happens again or if it was a one time thing...

---

