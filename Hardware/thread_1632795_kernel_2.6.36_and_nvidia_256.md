---
title: "kernel 2.6.36 and nvidia 256"
date: 2010-11-28
forum: Hardware
---

### Post by super.niels on 2010-11-28
Hey,
I had problems with my sound card, and had heard that i might help to update to kernel 2.6.36. Now my sound works, but i can't install the video driver for my video card. I have tried both the 256 and 260 nvidia driver, but neither of them can install. The problem is that both needs to be compiled with gcc 4.2, but apparently kernel 2.6.36 uses gcc 4.4.

So my question is, is it possible to get 2.6.36 to use gcc 4.2 or are there nvidia drivers that compiles with gcc 4.4?

Regards
Niels

---

### Post by Yellow Pasque on 2010-11-28
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=maverick)

---

### Post by super.niels on 2010-11-29
I have found a solution:-) Here on this web site [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup) 

what i did to make it work:
For some reason it wouldn't work when i just installed the drivers. I had to first enable the driver from "additional drivers", and then afterwards install the driver i have liked to here:

[http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb) 

and 

[http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb)

My computer is a sony vaio vpcs13m1e, with a geforce 310m video card, and it will not work with 260 driver which is the one that ubuntu installs but is happy with 256. 

Niels

---

