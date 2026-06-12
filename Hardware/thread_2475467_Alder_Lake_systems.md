---
title: "Alder Lake systems"
date: 2022-05-28
forum: Hardware
---

### Post by bjrosen on 2022-05-28
Has anyone built an Alder Lake system? If so which motherboard did you use and how did you get around the kernel problem? 22.04 is using the 5.15 kernel but everything I've read indicates that Alder Lake systems really need a 5.18 kernel. Were you able to install Ubuntu on an Alder Lake box, were you then able to install a 5.18 kernel? I also understand that the available 5.18 kernels are unsigned which won't work if you are using secure boot. I'm looking for a mother board that will support Alder Lake, DDR5 and has the ability to disable secure boot, a recommendation will be appreciated.

---

### Post by oldfred on 2022-05-28
I would look at Phoronix & its related site where they test the newest hardware with Linux.
[https://openbenchmarking.org/](https://openbenchmarking.org/)
Ubuntu 22.04 LTS is planning to use the Linux 5.15 kernel as its default, if Alder Lake CPU you may want newer kernel
[https://www.phoronix.com/scan.php?page=article&item=ubuntu-2204-alderlake&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-2204-alderlake&num=1)
DDR4 vs. DDR5 Memory Performance For Intel Core i5-12600K Alder Lake On Linux
[https://www.phoronix.com/scan.php?page=article&item=ddr4-ddr5-alderlake&num=1](https://www.phoronix.com/scan.php?page=article&item=ddr4-ddr5-alderlake&num=1)

---

### Post by aug7744 on 2022-05-28
You need change your topic title for an better description.
The main mainboards allow disable secure boot, but some notebook not allow disable it.
About kernel updates has PPAs with simple and easy ways to update your OS.

---

