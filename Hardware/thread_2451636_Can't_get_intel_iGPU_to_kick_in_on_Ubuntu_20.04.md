---
title: "Can't get intel iGPU to kick in on Ubuntu 20.04"
date: 2020-10-08
forum: Hardware
---

### Post by kmetz2 on 2020-10-08
Hi all, 

Can't get my graphics to work properly. I have an Intel i7 10th gen with an integrated iGPU. For two days I've been struggling with this. I followed guides on the Ubuntu Forums to edit the GRUB file. [IMG]https://ibb.co/yX5MCCt[/IMG][IMG]https://ibb.co/yX5MCCt[/IMG]See below. I'm really not sure what to do at this point as I've done a reinstall twice and still no result. I'm trying to disable the llvmpipe (LLVM 10.0.0, 256 bits).[IMG]https://i.ibb.co/37W8bb2/image.png[/IMG] [IMG]https://i.ibb.co/FB6089p/image.png[/IMG]
 [IMG]https://i.ibb.co/NY9W6rf/image.png[/IMG]


[IMG]https://i.ibb.co/xD95nbc/image.png[/IMG]

Any help is appreciated!

---

### Post by Yellow Pasque on 2020-10-08
Please share the text of your /var/log/Xorg.0.log file. (Copy/paste the text between code tags. No giant screenshots please).

Alternatively, you can run this to generate bug report and automatically gather relevant logs if you have a Launchpad account:
```
ubuntu-bug graphics
```

---

