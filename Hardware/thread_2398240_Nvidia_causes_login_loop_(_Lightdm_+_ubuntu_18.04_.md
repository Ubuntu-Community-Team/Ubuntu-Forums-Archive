---
title: "Nvidia causes login loop ( Lightdm + ubuntu 18.04 + kernel 4.15 )"
date: 2018-08-09
forum: Hardware
---

### Post by hmoez on 2018-08-09
Good day everyone,

After installing ubuntu 18.04 on my HP Omen ( Nvidia GTX 1050 ) I tried plugging in an external monitor via HDMI but it didn't detect it.

the lspci command returns : 01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)so I tried installing Nvidia Drivers through 


[LIST=1]
[*]ubuntu-drivers install
[*]apt-get install nvidia-driver-*
[*]nvidia.RUN files
[/LIST]
I tried the 390, 375, 396, 340 following multiple threads about this problem but it always ends up with the same thing, I get to the login screen, enter my password and it loop back to the login screen so I remove all the nvidia packages and reboot in order for me to get back to the Desktop.

As it's stated in the title : I am using LIGHTDM , ubuntu version 18 and the kernet version 4.15.

Thank you.

---

