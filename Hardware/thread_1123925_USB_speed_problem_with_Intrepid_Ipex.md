---
title: "USB speed problem with Intrepid Ipex"
date: 2009-04-12
forum: Hardware
---

### Post by MiKu on 2009-04-12
I'm having a weird problem with my external USB hard drive in Ubuntu 8.10. The problem is that data transfer to/from the USB drive is extremely slow (around 3-4 MB/s) when the drive is plugged into one of the rear USB connectors connected directly to the motherboard. However, if I plug the drive into one of the USB connectors located in the front panel of the computer the drive operates on appropriate USB 2.0 speeds.

The USB drive is Fujitsu Siemens StorageBird XL 250GB and my motherboard is Intel DP43TF. I tested the drive with LiveCDs of Ubuntu 8.04 and 9.04 and, to my surprise, it worked fine with the former and didn't work in the latter. The drive also works fine in Vista from both the front and rear connectors. Other USB devices also seem to work fine irrespective of the port used.

Any ideas on how to make the drive work also using the rear connectors? My guess is that one of the two USB controllers on the motherboard is not working properly and hence the problem with the rear ports but I'm not sure how to begin solving the problem since according to both dmesg and lsusb everything seems to be in order.

---

