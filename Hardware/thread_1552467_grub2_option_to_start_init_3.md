---
title: "grub2 option to start init 3"
date: 2010-08-13
forum: Hardware
---

### Post by xtracool_protik on 2010-08-13
Does anyone know? y'day I activated ati on one of my friends laptop and on boot we get is nothing (blank screen) ctrl+alt+f1/f2 or f7/f8 doesn't work.
 I deleted xorg.conf by logging through live cd and mounting system drive but that didn't help. I tried quite many things (disabling gdm by deleting it) the similar way but nothing seems to help at all :(
 I wouldn't mind just reinstalling but that is project machine apart from taking backup just setting it back up as it was will take quite some time.
 I would like some opinions about the problem
 Thanks

```
lspci | grep VGA
``` while logged in live cd
shows both ATI radeon HD 36xx and Intel

---

### Post by xtracool_protik on 2010-08-25
Hey fixed it,
 Just so anyone reading through this thread know:
 The laptop was Lenovo T series with dual graphics card and OS switching capability.
 Need to disable switching in BIOS to get it working 
 Current setting - Discrete graphics card and in use card - PCIe slot

---

