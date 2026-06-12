---
title: "Nvidia 195.xx unable to find Kernel source tree?"
date: 2010-05-19
forum: Hardware
---

### Post by LanternInc on 2010-05-19
I'm trying to manual install nvidia 195 driver, but it gives me an error:

"Unable to find kernel source tree (and so on)".

Please help.

---

### Post by ankit singh on 2010-05-19
install kernel source which matches your running kernel via synaptic.
u can check ur kernel version by typing the foll code in terminal
```
uname -r
```after this close x and run the nvidia installer.

---

### Post by LanternInc on 2010-05-19
It works now. I forgot these:

sudo apt-get install build-essential linux-headers-`uname -r`


Thanks

---

