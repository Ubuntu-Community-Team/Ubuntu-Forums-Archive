---
title: "Custom Kernel can't boot to init 3"
date: 2022-06-20
forum: Hardware
---

### Post by manmath on 2022-06-20
Hi All, with my custom build kernel I can't boot into init 3 (text console) though there's no problem booting into plasma desktop. Does framebuffer config have anything to do with it? Here's config file lines about framebuffer:

# Frame buffer Devices
#
CONFIG_FB_CMDLINE=y
# CONFIG_FB is not set
# end of Frame buffer Devices

---

### Post by manmath on 2022-06-21
I could log into init 3 with "vga=normal nomodeset" option, but the resulting console is of very low resolution. Is any workaround possible here?

---

