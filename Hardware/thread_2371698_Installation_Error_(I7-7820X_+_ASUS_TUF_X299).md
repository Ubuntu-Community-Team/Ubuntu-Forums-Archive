---
title: "Installation Error (I7-7820X + ASUS TUF X299)"
date: 2017-09-17
forum: Hardware
---

### Post by bachie on 2017-09-17
-CPU : Intel I7-7820X
-M/B : ASUS TUF X299
-RAM : G.Skill DDR4 PC4-28800 32GB (8GB X 4)
-SSD : ADATA XPG SX800 M,2 NVMe 512GB
-VGA : Nvidia GTX 1050 2GB

I tried to install Ubuntu 16.04 to this system using usb memory.
but after installation the system is not bootable.
Didn't current linux distribution support new CPUs yet ?
Please let me know how to install Linux to my system.

Thank you.
Bach

---

### Post by Yellow Pasque on 2017-09-18
> Didn't current linux distribution support new CPUs yet?

More likely, it's an issue with the GTX 1050.
Try booting with 'nomodeset' parameter. Then you can install the nvidia driver. I'm not sure if the version in Ubuntu's repo is new enough. You may need to use [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Hopefully, someone else can comment on that.

---

