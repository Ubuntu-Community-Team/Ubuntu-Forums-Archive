---
title: "Enable DMA support"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by redman5087 on 2005-06-19
Hi, I'm trying to enable "DMA" support on my Ubuntu Machine!
When I try to 

"sudo hdparm -d1 /dev/hda",

 I get 

   /dev/hda:
      setting using_dma to 1 (on)
      HDIO_SET_DMA failed: Operation not permitted
      using_dma    =  0 (off)

After searching Google, I found some answers!
I have a "VIA mainboard", I think this is the reason why It won't enable "DMA"
Do I have to Enable VIA support in the kernel, can this be done with a module?
I have read somthing about a " via82cxxx" module?

How do I fix this problem with Ubuntu?

Kind regards 

Redman

---

### Post by jeremy on 2005-06-19
[http://ubuntuforums.org/showpost.php?p=93238&postcount=5](http://ubuntuforums.org/showpost.php?p=93238&postcount=5) has the answer you need.

---

