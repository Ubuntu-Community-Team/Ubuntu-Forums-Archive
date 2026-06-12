---
title: "Cannot switch to NVIDIA graphics card"
date: 2019-08-09
forum: Hardware
---

### Post by koalemos13 on 2019-08-09
Hi everyone,
I have Ubuntu 18.04 installed on my Lenovo ideapad 520S (which has a Geforce 940MX). To use my graphics card, i installed the nvidia-driver-430 (which worked).
However, now when I open up NVIDIA X Server and switch to the NVIDIA profile, it shows the NVIDIA profile as selected, but it still uses the Intel graphics, even after logout or reboot.
I didn't find any problems with my driver (nvidia-smi displays my graphics card), so I'm unsure where this problem could be coming from.

Have any of you had this problem before or know what the cause could be?
Thanks a lot :)

---

### Post by Autodave on 2019-08-09
Have you checked the BIOS to see if you have the option in there of disabling the Intel (onboard) GPU?

---

### Post by koalemos13 on 2019-08-10
There is no option to disable any GPU, i can only change between switchable or discrete graphics (neither of which works though).

---

### Post by mastablasta on 2019-08-12
are you using bumblebee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

optirun is the command to switch to using discrete GPU.

---

