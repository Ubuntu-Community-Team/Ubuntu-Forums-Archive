---
title: "SATA issue"
date: 2008-07-15
forum: Hardware
---

### Post by macnyak on 2008-07-15
from my post:

[http://ubuntuforums.org/showthread.php?t=859491](http://ubuntuforums.org/showthread.php?t=859491)


a helpful link on this site:

[http://www.phoronix.com/scan.php?page=article&item=nvidia_8200_mobos&num=4](http://www.phoronix.com/scan.php?page=article&item=nvidia_8200_mobos&num=4)




which states that:

System Setup:

As we mentioned in our GeForce 8200 IGP review, this chipset has a few issues currently with Linux. If you are using a Linux distribution that ships with a pre-2.6.25 Linux kernel, the Serial ATA support will likely go undetected. This means you will have a tough time using Ubuntu 8.04 LTS or other distributions from earlier this year unless using a separate PCI/PCI-E disk controller to get you started or building a new kernel first. The distribution we were successful using with the NVIDIA MCP78S "out of the box" was Fedora 9.

[B]
How can I fix that issue?[/B]

does it mean that i cannot use and enjoy Ubuntu OS on a PC that i will build?

---

### Post by Dark_Stang on 2008-07-15
You need to get a 2.6.25 or newer kernel in an ISO. Since your posting I assume you have a computer you can use to do this...
Links to 2.6.26 kernel packages
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux+2.6.26](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=linux+2.6.26)
How to make your own Ubuntu ISO
[http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/](http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/)

---

### Post by jimv on 2008-07-15
Ok, I just looked at the manual for your motherboard.  If you look on page 35, it shows the Integrated Peripherals screen in the BIOS.  There is an option there for SATA Mode Select, which you can set to RAID, AHCI, or IDE.  If you set it to IDE, Ubuntu will be able to see your SATA drive like an IDE drive, and it should be ok.

Note:  You probably shouldn't change this option after you have Ubuntu installed, because it MIGHT stop Ubuntu from booting.

---

