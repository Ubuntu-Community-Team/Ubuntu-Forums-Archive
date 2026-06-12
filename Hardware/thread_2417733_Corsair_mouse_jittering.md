---
title: "Corsair mouse jittering"
date: 2019-04-26
forum: Hardware
---

### Post by aoto-san on 2019-04-26
Hello,

My corsair harpoon mouse jitters in ubuntu 19.04 but not in windows 10. I tried a generic chinese mouse and it worked just fine. I installed ckb-next and played around with the dpi and sensitive settings but had zero improvement.

example
[ATTACH=CONFIG]283108[/ATTACH]

I had trouble getting my usb ports to work correctly, Apparently it's a gigabyte 970A-UD3P and 970A-DS3P motherboard problem. Had to enable iommu in the uefi to be able to install ubuntu, otherwise my usb 2.0 ports wouldn't work. After the installation I added GRUB_CMDLINE_LINUX="iommu=soft" to grub and then disable iommu in the uefi

---

### Post by aoto-san on 2019-04-28
I haven't found anything in the last 2 days that could help me with it.

---

