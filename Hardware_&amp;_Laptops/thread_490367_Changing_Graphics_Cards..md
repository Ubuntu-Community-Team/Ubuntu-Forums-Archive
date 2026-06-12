---
title: "Changing Graphics Cards."
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by ErusGuleilmus on 2007-07-02
How do I switch graphics cards and make it so that the xserver detects them? I had an ATI and switched it out with an NVidia. I then got a message saying that the xserer failed beacuse no display device was detected and then was stuck with command line insterface. How do I solve this? 

    Thanks.

---

### Post by teaker1s on 2007-07-03
```
sudo dpkg-reconfigure xserver-xorg
```
Depending on the model of the nvidia card you may need either

1)May work with "nv" as selected driver-note no open gl-this can be rectifed when you have desktop again with synaptic to install open gl driver from repositories and reconfigure xserver for "nvidia"
2)nvidia beta driver from nvidia

---

