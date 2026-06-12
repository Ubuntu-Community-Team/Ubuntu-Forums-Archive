---
title: "HOWTO: Use more than 3GB RAM on 32-bit Ubuntu 8.04"
date: 2008-06-16
forum: Hardware
---

### Post by edmondt on 2008-06-16
I found this tip somewhere, and its so nice to able to use the full 4GB on my laptop without installing the 64bit Ubuntu, I just want to share it:

sudo apt-get install linux-restricted-modules-server linux-ubuntu-modules-2.6.**24-18**-server linux-image-2.6.**24-18**-server linux-headers-server linux-image-server linux-server


Replace **24-18** with the most current version as needed. nvidia drivers should work too...

---

### Post by chris7cmcc on 2009-05-07
Thanks this worked for me--just wanted to give some feedback.

apt-get install linux-restricted-modules-server linux-ubuntu-modules-2.6.24-24-server linux-image-2.6.24-24-server linux-headers-server linux-image-server  linux-server

---

### Post by bacardiandwatermelon on 2009-05-08
Aren't those Hardy Server Kernels? I would have thought installing Jaunty 64bit would have been easier..

---

