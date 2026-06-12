---
title: "Laptop ASUS N53S gfx card problems"
date: 2013-02-04
forum: Hardware
---

### Post by VoltureX on 2013-02-04
Hi.

I'm running 10.04 LTS

I can't get my graphics cards to work. There are 2 integrated.

Intel 4000 and NVIDIA GT 630M

I have installed the nvidia driver by this command:
sudo apt-get install nvidia-current

I can see the drivers are installed from: Hardware Drivers under administration.

The way I have tested it is by using some of the GL screensavers and they are very slow. If I get the NVIDIA card to work I presume the GL screensavers will run a lot faster.

What can I do to activate the NVIDIA card in my system under Ubuntu 10.04 LTS?

Thanks

Volt.

---

### Post by Yellow Pasque on 2013-02-04
Remove the nvidia driver. That is not the correct way to install it on an Optimus system. Once your graphics work again, then you can follow:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

>  If I get the NVIDIA card to work I presume the GL screensavers will run a lot faster.
Only if you run them on the nvidia card (using optirun command).

---

### Post by VoltureX on 2013-02-04
Thanks a lot. It worked out perfectly ;)

---

