---
title: "edgy problems with madWIFI"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by superITgeek on 2006-10-29
Hello all,

I went ahead and did a clean install of Edgy on my Toshiba Satellite laptop. For some reason the new madwifi driver does not seem to work as well as the previouse version in Dapper.

I know that if I want to build the madwifi driver myself I need to use the same version of GCC that was used to compile the kernel, how do I find out which version was used to compile the kernel?

Also, do I need to remove some packages before compiling the driver myself?

I do some wireless auditing with my laptop and need the madwifi driver to support packet injection and monitor mode.

Thanks you!

EDIT: I think I might have found something to try; [http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)
will give it a shot and let you know!

---

### Post by superITgeek on 2006-10-30
Okay, I did the mentioned howto and was able to patch and compile the madwifi drivers. However, when trying to load the module I get the error;

FATAL: Error inserting ath_pci [/lib/modules/2.6.17-10-generic/net/ath_pci.ko] Unknown symbol in module, or unknown perameter.

Is this maybe due to using a differant version of GCC to compile the module than was used to compile the kernel? If so, any recomendations on how to build a working module?

Thanks!

---

### Post by tamasrepus on 2006-10-31
Try loading the ath_hal module first.

---

