---
title: "Realtek 1220 Audio Driver - Where?"
date: 2017-04-25
forum: Hardware
---

### Post by foxdanger on 2017-04-25
I have a Gigabyte z270x Aorus Gaming 5 and the audio driver is not working on Ubuntu.

Saw thousand of topics here and around internet and didn't find how to install the Realtek Audio Driver on Ubuntu.

It has a way to make it works?

---

### Post by pete-br on 2017-04-26
You are experiencing a hardware problem. You should have posted the question in the hardware section.

You motherboard has the ALC1220 Audio chip. It's supported starting from kernel version 4.11.
This kernel version is still in development, but expected to be stable very soon.
You could use the 4.11 version if you figured out how to install it.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.11-Sound-Updates](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.11-Sound-Updates)
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.11-rc8-Released](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.11-rc8-Released)

---

### Post by slickymaster on 2017-04-26
Thread moved to ***Hardware*** for a better fit

---

### Post by Yellow Pasque on 2017-04-26
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by pete-br on 2017-04-28
The Realtek ALC 1220 driver is part of the kernel. To 'install' that driver you must therefore upgrade to a newer kernel.

Here is how to do that: [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Preparing_to_install_an_upstream_kernel](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Preparing_to_install_an_upstream_kernel)

It will take you a little bit to figure out. But in the end it's not so hard.

---

### Post by Yellow Pasque on 2017-04-28
> **pete-br said:**
> The Realtek ALC 1220 driver is part of the kernel. To 'install' that driver you must therefore upgrade to a newer kernel.

The link I posted allows one to upgrade the driver for the current Ubuntu kernel.

---

### Post by hound5777 on 2017-08-21
Any ideas why it wouldn't work with 4.11+ and firmware 1.164.1?

---

### Post by Yellow Pasque on 2017-08-21
Did you try upgrading ALSA modules as described before? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
There have been some ALC1220 fixes for specific mobos/systems in newer kernels.

Give more info might help too: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

