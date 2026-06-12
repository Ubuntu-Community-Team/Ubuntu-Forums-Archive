---
title: "video card driver help."
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by Dethis on 2008-02-21
hey

how do i find a video card driver for linux?

i have mobile intel graphics media accelarator x3100

---

### Post by Fechter on 2008-02-21
I think there were intel vc drivers in the updates.. make sure you have "recommended updates" turned on then
sudo apt-get update
sudo apt-get upgrade
Then you should have it.

---

### Post by Yellow Pasque on 2008-02-21
The xserver-xorg-video-intel driver is installed by default on Ubuntu. See this if you're trying to use Compiz with it: [http://ubuntuforums.org/showpost.php?p=4169228&postcount=14](http://ubuntuforums.org/showpost.php?p=4169228&postcount=14)

---

