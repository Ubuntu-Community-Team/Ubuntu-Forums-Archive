---
title: "AMD Radeon HD 7950"
date: 2014-05-23
forum: Hardware
---

### Post by piotrknetka on 2014-05-23
I get an error while openning Steam: 
OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit [https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457](https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457).

using sudo amdconfing --initial returns:
No supported adapters detected

installed fglrx-updates.
Ubuntu 14.04 LTS 64-bit
3.14.4-031404-generic

btw I have had installed nvidia drivers for my gtx 460, untill I installed ati gpu and drivers.

---

### Post by lukeiamyourfather on 2014-05-23
What GPU do you actually have? Chances are you don't need both the Nvidia and AMD drivers. If you have a Radeon HD 7950 like the thread title says then it should work with the AMD drivers in the Ubuntu repositories. Don't install drivers from AMD website, go through the Ubuntu repositories.

---

