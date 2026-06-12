---
title: "Low write speeds on NVMe drives"
date: 2022-11-23
forum: Hardware
---

### Post by hyphaed on 2022-11-23
Hi people

I'm on Ubuntu 22.04 LTS

I'm having issues with my M2 Nvme drives

I do have 2 of them, one plugged to PCIe 3.0 M2 port, another to PCIe 4.0 M2 port, the benchmarks say write speed 257 Mb/s (PCIe 3) and 505 Mb/s (PCIe 4)

it should be x10 that write speeds on both disks

yet  those speeds would be good enough if real (although far from the real  speeds of those M2). The problem is that the real write speed is about  35 to 60 Mb/s when copying large files

anyone with the same problem? anyone knows how to solve it?

I wrote to Samsung but they gave me no good response about it, they just told me the drivers are optimized for Windows

I've checked intel optane guide since it talks about NVMe, yet haven't been able to fix the issue
[https://community.intel.com/t5/Blogs/Products-and-Solutions/Memory-Storage/Tuning-the-performance-of-Intel-Optane-SSDs-on-Linux-Operating/post/1334953](https://community.intel.com/t5/Blogs/Products-and-Solutions/Memory-Storage/Tuning-the-performance-of-Intel-Optane-SSDs-on-Linux-Operating/post/1334953)

also checked Debian wiki
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)


benchmarks Samsung 970 Evo Plus
[https://www.dropbox.com/s/mhsjr9tpxfpy3ln/970evoplus.png?dl=0](https://www.dropbox.com/s/mhsjr9tpxfpy3ln/970evoplus.png?dl=0)


benchmarks Samsung 980 Pro
[https://www.dropbox.com/s/u3gwh849sw3aba3/980pro.jpg?dl=0](https://www.dropbox.com/s/u3gwh849sw3aba3/980pro.jpg?dl=0)

---

### Post by oldfred on 2022-11-24
Your report says MB per sec, not Mb per second. 
Drives often specify bits per second, but we really want to write bytes.

---

### Post by oygle on 2022-11-24
Samsung doesn't seem to have made much of a contribution to firmware, see [https://fwupd.org/lvfs/vendors/#samsung](https://fwupd.org/lvfs/vendors/#samsung) . What brand are the SSD's ? Not much at [https://fwupd.org/lvfs/search?value=+M2+Nvme](https://fwupd.org/lvfs/search?value=+M2+Nvme) to help but a Vendor name is better for searching.

Quite a lot of posts at [https://duckduckgo.com/?q=Low+write+speeds+on+NVMe+drives+&t=newext&atb=v336-1&ia=web](https://duckduckgo.com/?q=Low+write+speeds+on+NVMe+drives+&t=newext&atb=v336-1&ia=web)

This one may be the same model ? - [https://eu.community.samsung.com/t5/computers-it/samsung-980-pro-500gb-nvme-m2-drive-very-low-write-speeds/td-p/2531948](https://eu.community.samsung.com/t5/computers-it/samsung-980-pro-500gb-nvme-m2-drive-very-low-write-speeds/td-p/2531948)

Great point made from [https://forums.tomshardware.com/threads/extremely-slow-write-speed-m-2-nvme.3731026/](https://forums.tomshardware.com/threads/extremely-slow-write-speed-m-2-nvme.3731026/)

> People tend to forget write speeds depend on what is writing to the SSD.

---

### Post by oldfred on 2022-11-24
Samsung 980 NVMe SSD Linux Performance (non-PRO)
[https://www.phoronix.com/scan.php?page=article&item=samsung-980-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=samsung-980-linux&num=1)
Samsung 980 PRO PCIe 4.0 NVMe SSD Linux Performance Oct 2020
[https://www.phoronix.com/scan.php?page=article&item=samsung-980-pro&num=1](https://www.phoronix.com/scan.php?page=article&item=samsung-980-pro&num=1)

For my Samsung NVMe drives I download the ISO with a newer firmware.
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.

To see firmware Revision - FW Rev and compare by model to available ISO. 
sudo apt install nvme-cli
sudo nvme list
or
udisksctl status

---

