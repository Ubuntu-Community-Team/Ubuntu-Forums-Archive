---
title: "canon mx320 no work on ubunto 64"
date: 2010-01-28
forum: Hardware
---

### Post by neversleep54 on 2010-01-28
canon mx320 no work on ubunto 64 what can i do ?

i have download the driver for the web but it write me error architecture i386.

please HELP HELP HELP ME !!!!

---

### Post by manu7irl on 2010-05-14
That did the trick for me on Ubuntu 10.04 64 bit!
Simply run in terminal from the folder where you placed the 2 packages :

Code:

```
sudo dpkg -i --force-architecture ./cnijfilter-common_3.10-1_i386.deb
```

and then :

Code:

```
sudo dpkg -i --force-architecture ./cnijfilter-mx320series_3.10-1_i386.deb

```




Emmanuel.

Pc configuration :
motherboard : gigabyte GA-MA785G-UD3H
processor : AMD Athlon II quad core 630 2.80Ghz
memory : 2 x 2 Gb DDR2 800Mhz
video card : onboard ATI HD4200
OS : dualboot grub2 Ubuntu 10.04 64bits / Windows 7 32 bits

---

