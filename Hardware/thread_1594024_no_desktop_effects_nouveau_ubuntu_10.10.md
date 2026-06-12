---
title: "no desktop effects nouveau ubuntu 10.10"
date: 2010-10-11
forum: Hardware
---

### Post by lnxr0x on 2010-10-11
I've got 10.10 up and running on an older machine with an Nvidia GF4 MX440. 
I'm experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974)

.. so I decided to install the nouveau GL support by running the following: 
sudo apt-get install libgl1-mesa-dri-experimental 

I confirmed GL support by running "GLXgears", performance wasn't great, but it worked.

I still can't enable desktop effects !! I don't care about the desktop cube, but the "no effects" option just feels "clunky" .. could be the card is just too slow or I'm missing some package. 

any help would be great .. thanks in advance :)

---

