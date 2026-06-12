---
title: "about hibernation with too small swap"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by jwaiwit on 2009-11-02
Actually my karmic did good except have to prepend dns. But i just understand the problem why i can't hibernation is my swap is too small. My ram is 2GB ,but swap is 510M. 
  
I just curious could i change Hibernation file to store in my root (/) file instead in swap.

The hardest thing is , I already formatted and complete installation ready. don't want to move or increased partition anymore.


Thanks

---

### Post by Perturbed Penguin on 2009-11-17
As far as resizing goes you can use gparted-live. Just boot into it and you can resize your swap area... depending on how you installed you may have to make your main Ubuntu partition smaller first so you have room to add to your swap but after that you can resize your main partition to fill the extra space. Hope this helps. ;)

---

### Post by efflandt on 2009-11-17
Someone did post a HOWTO use a swapfile instead of swap partition for hibernate.

[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

