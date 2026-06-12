---
title: "ubuntu 13.10 black screen after installing nvidia optimus drivers, GeForce GTX 765M"
date: 2014-02-06
forum: Hardware
---

### Post by James_Burrows on 2014-02-06
I have a 3XS Graphite LG155 laptop from Scan, which has integrated intel graphics along with an NVIDIA GeForce GTX 765M graphics card.


Initially when installing Ubuntu 13.10 desktop 64-bit the setup was freezing but I managed to install OK by setting the nomodeset boot option at the start of the install).


My laptop is using the the integrated graphics now with the following driver: -
Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits)


I'm running Kernel 3.11.0-12-generic and Gnome 3.8.


I've attempted to install the nvidia drivers doing the following: -


    sudo add-apt-repository ppa:xorg-edgers/ppa
    sudo apt-get update
    sudo apt-get install nvidia-331


This seemed to install fine however after a reboot all I get is black screen, and I have to use another terminal to uninstall the drivers before I get a desktop back again.


I've also tried installing earlier nvidia drivers through apt-get but with the same issues.


Any help appreciated.


Thanks

---

### Post by Yellow Pasque on 2014-02-07
You can't just install nvidia drivers directly on an Optimus system. Check out Bumblebee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by James_Burrows on 2014-02-07
Hi, thanks for the reply.

For anyone with the same issues, I've managed to get it working by first running: -

> sudo apt-get remove nvidia*

Then following the instructions here: -
[http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271](http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271)

Although nvidia-settings-331 does not seem to exist... anyone know where to get it?

Thanks again

---

