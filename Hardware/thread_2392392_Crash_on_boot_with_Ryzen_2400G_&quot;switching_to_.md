---
title: "Crash on boot with Ryzen 2400G: &quot;switching to amdgpudrmfb from EFI VGA&quot;"
date: 2018-05-20
forum: Hardware
---

### Post by mfleming on 2018-05-20
Hi,

I am trying to get Ubuntu 18.04 to work reliably on a new computer with a Ryzen 2400 CPU/GPU. Sometimes the boot completes, but very often it fails with the message:
"switching to amdgpudrmfb from EFI VGA". This happens about the same time screen modes would change, and with the nomodeset boot parameter the boot never fails. From what I've found online this has something to do with the GPU's firmware, and the "firmware-amd-graphics" package is supposed to fix it, but I have not been able to find this package for installation, despite enabling non-free sources. I have also tried downloading AMD's proprietary driver from their website, but the installation process does not complete.

I suppose I could disable the built-in GPU in the BIOS and switch to an Nvidia graphics card, but I'd prefer to use what I've already paid for, if possible.

Thanks in advance for your help.

Matthew Fleming

---

### Post by P-I H on 2018-05-21
Read this article. Perhaps it will get you some information about how to solve the problems.
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1)

---

### Post by experimancer on 2018-05-27
You have to use kernel 4.17 or newer to install, boot and run (mostly) any Linux distro in AMD Ryzen5 2400G builds. With lower kernel version (the one in Ubuntu 18.04 is 4.15) you will not succeed fully to run your machine in full HD graphics modes

---

