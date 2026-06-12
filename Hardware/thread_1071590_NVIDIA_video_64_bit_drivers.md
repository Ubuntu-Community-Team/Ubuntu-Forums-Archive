---
title: "NVIDIA video 64 bit drivers ?"
date: 2009-02-16
forum: Hardware
---

### Post by wizguys on 2009-02-16
Is GEFORCE 9600 GSO video card supported in Unbuntu 8.10 64 bit ?

I have tried 173, 177, 180.22 180.29 and none seem to work.

Has anybody being able to make it work, if yes how ?

---

### Post by ridetheteapot on 2009-02-16
install from nvidia's bins at [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.29/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.29/)

[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.29/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.29/README/appendix-a.html)
GeForce 9600 GSO 	0x0610

most good info is here [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.29/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.29/README/index.html)

you'll probably want to use *pkg3.run


--- If you tried already check something out
lspci -n | grep `lspci | grep VGA | cut -b -7`
whats the last 3 numbers? 610? or not?

---

