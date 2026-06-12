---
title: "Gigabyte Aorus Z490 motherboards and Ubuntu"
date: 2021-01-22
forum: Hardware
---

### Post by cscj01 on 2021-01-22
Is anyone successfully using one of the above mentioned mobos with Ubuntu 18.04 or higher?  I am going to upgrade my build, and I want to be sure these mobos work.  I have used a Z77X-UD5H for a long while, and I think it's time I moved to a newer platform.

Also, I am not a gamer, but I do a lot of Darktable, Audacity, VueScan, and MySQL database  processing.  So if there are some of you who are using any of these mobos and have a recommendation as to which mobo might be the best fit for me, I would appreciate your input.  I have always used Intel, so I most likely will stick with them.  Thanks for any suggestions.

---

### Post by simon-webb on 2021-01-22
Hi there. I'm not running this (Ubuntu 20.04) system on it, but I have a Debian 10 system on a Gigabyte Z490 Vision D which looks (from an online comparison) to be very similar, with no problems at all. I haven't tested SLI, Crossfire, or RAID, but have got a big fat RTX2080Ti in there with a couple of recent NVMe drives and those and the Bluetooth and WiFi all work straight out of the box, as does the 7.1 surround (through HDMI, at least). Maybe double-check the WiFi as that's something that can occasionally differ between otherwise similar motherboards in ways that matter (very recent chipsets occasionally lack Linux support for a year or two)...you'll probably find confirmation that it has Linux support (and if it has Linux support, that's all that matters...new kernel drivers can be plugged into any distro)...or, if you can't find evidence of that, it will be enough if you can find that the chipset Gigabyte are using in the Aorus is the same as the one they use in the Vision D, because I can confirm that the Vision D's WiFi (and Bluetooth) definitely works with Linux.

---

### Post by oldfred on 2021-01-22
This site tested it and has some comments.

Gigabyte Z490 with 20.04 needs kernel update  to 5.6 for Ethernet to work.
[https://www.phoronix.com/scan.php?page=article&item=intel-10500k-10900k&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-10500k-10900k&num=1)

---

### Post by cscj01 on 2021-01-22
> **simon-webb said:**
> Hi there. I'm not running this (Ubuntu 20.04) system on it, but I have a Debian 10 system on a Gigabyte Z490 Vision D which looks (from an online comparison) to be very similar, with no problems at all. I haven't tested SLI, Crossfire, or RAID, but have got a big fat RTX2080Ti in there with a couple of recent NVMe drives and those and the Bluetooth and WiFi all work straight out of the box, as does the 7.1 surround (through HDMI, at least). Maybe double-check the WiFi as that's something that can occasionally differ between otherwise similar motherboards in ways that matter (very recent chipsets occasionally lack Linux support for a year or two)...you'll probably find confirmation that it has Linux support (and if it has Linux support, that's all that matters...new kernel drivers can be plugged into any distro)...or, if you can't find evidence of that, it will be enough if you can find that the chipset Gigabyte are using in the Aorus is the same as the one they use in the Vision D, because I can confirm that the Vision D's WiFi (and Bluetooth) definitely works with Linux.Thanks for the info.  I will check out the Aorus vs Vision.

---

### Post by cscj01 on 2021-01-22
> **oldfred said:**
> This site tested it and has some comments.

Gigabyte Z490 with 20.04 needs kernel update  to 5.6 for Ethernet to work.
[https://www.phoronix.com/scan.php?page=article&item=intel-10500k-10900k&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-10500k-10900k&num=1)
[QUOTE}    For more info on UEFI boot install & repair - Regularly Updated :
    [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
    Please use Thread Tools above first post to change to [Solved] when/if answered completely[/QUOTE]

Some good info in the link.  Thanks.

---

### Post by simon-webb on 2021-01-23
It's no problem re 5.6 or later for ethernet...5.8 is already here (in 20.04).

---

