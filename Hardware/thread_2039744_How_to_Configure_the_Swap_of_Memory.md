---
title: "How to Configure the Swap of Memory"
date: 2012-08-09
forum: Hardware
---

### Post by huangyingw on 2012-08-09
Hi,
  I am using a SSD with 8G memory, and the swap partition is 16G.
  I use htop to inspect the usage of my memory. And I find that, once the memory usage go above 4G, the Ubuntu use begin to swap some memory into swap, and stop to use more memory, only stop at around 4G. 
  My ubuntu is 64 bit, so, it could certainly use up to 8G.
  Is there a place to configure that, only after the memory usage is above 7G, than ,begin to swap memory into swap partition. Otherwise, it would be a great waste of my 8G memory. 
  Disabling the swap partition is the simplest way. But I need to keep swap partition, for I need to enable hibernate feature.

---

