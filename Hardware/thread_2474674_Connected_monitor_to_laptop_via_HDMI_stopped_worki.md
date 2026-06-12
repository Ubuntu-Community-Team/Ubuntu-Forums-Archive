---
title: "Connected monitor to laptop via HDMI stopped working"
date: 2022-05-05
forum: Hardware
---

### Post by poulfly on 2022-05-05
Hello everyone, after the update, the monitor connected to the laptop via HDMI stopped working. I needed to update the software, I updated according to this guide - [https://www.vultr.com/docs/update-ubuntu-server-best-practices](https://www.vultr.com/docs/update-ubuntu-server-best-practices)
 After the update the next day, when I turned on the laptop, the monitor was detected, but there was a black screen, when the Join Displays option was selected and after pressing the Apply button, the settings were still reset to the Single Display option.  (screenshot - [https://joxi.net/ZrJKoLFQxq7Vmj](https://joxi.net/ZrJKoLFQxq7Vmj))

My System
OS: Ubuntu 20.04 focal
Kernel: x86_64 Linux 5.13.0-40-generic
DE: GNOME 3.36.5
CPU: AMD Ryzen 7 5800H
GPU: AMD/ATI
GPU2: RTX3060
Laptop Lenovo Legion 5-15ACH6H

A similar problem was when I installed the latest NVIDIA driver in the driver settings after installing the OS. After that, the monitor turned off and didn&#8217;t work anymore, the problem was fixed only by reinstalling the OS (I don&#8217;t really understand the intricacies of Ubuntu). I just reinstalled the OS and did not touch the drivers, the driver was selected by default after installation and everything worked fine until the system update, which is described above.


Windows is installed on this laptop and now both monitors work correctly as before.

---

### Post by mhgsys on 2022-05-14
Try Setting the Prime Profile to NVIDIA performance mode from the NVIDIA X Server settings
[IMG]https://i.stack.imgur.com/ks4Wk.png[/IMG]

---

