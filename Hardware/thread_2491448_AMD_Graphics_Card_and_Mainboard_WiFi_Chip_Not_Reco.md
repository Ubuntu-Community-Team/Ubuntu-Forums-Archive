---
title: "AMD Graphics Card and Mainboard WiFi Chip Not Recognized After Kernel Update"
date: 2023-10-09
forum: Hardware
---

### Post by Trash_Gordon on 2023-10-09
Hi,
with kernel versions > 6.2.0-27, my on-mainboard wifi/bluetooth feature no longer work. Additionally, the graphics card (Radeon RX 6800) only outputs a very low resolution.

I hope all useful information is contained in the system-info output:
[LIST]
[*][Working 6.2.0-27]("https://paste.ubuntu.com/p/3mvyDkc9Rq/")
[*]Broken 6.2.0-34: [ATTACH]292843[/ATTACH]
[/LIST]

---

### Post by chtorogu on 2023-10-09
I had a kernel update bork my HTPC like that a few months ago. Rebooted after update (just "sudo apt upgrade") and practically all drivers were gone. I found the solution though. It was to download and install the linux-modules-extra package (the one appropriate for the kernel version.)

The one for 6.2.0-34 can be downloaded here: [https://packages.ubuntu.com/jammy/amd64/linux-modules-extra-6.2.0-34-generic/download](https://packages.ubuntu.com/jammy/amd64/linux-modules-extra-6.2.0-34-generic/download)

---

### Post by Trash_Gordon on 2023-10-10
Wow that was easy...

Thanks you, that was exactly the problem. linux-modules-extra package was installed for the working 6.2.0-27, but was missing for the newer versions. Installing linux-modules-extra package-6.2.0-34 fixed it.

---

