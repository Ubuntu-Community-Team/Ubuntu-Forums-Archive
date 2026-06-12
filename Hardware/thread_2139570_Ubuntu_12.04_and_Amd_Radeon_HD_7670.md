---
title: "Ubuntu 12.04 and Amd Radeon HD 7670"
date: 2013-04-27
forum: Hardware
---

### Post by abhich on 2013-04-27
is ubuntu 12.04 compatible with Radeon HD 7670 ?

Please help

---

### Post by abhich on 2013-04-27
please help ... 
my laptop is not being able to recorgnise my graphics card !!

---

### Post by Bashing-om on 2013-04-27
abhich; Hi !

Not much info provided in order to to help you .

What are the symptoms? What is happening or not happening >

I did A and B expecting X to happen but instead Y resulted.
Then this info is helpful; Post the output of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga
```[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Mark Phelps on 2013-04-27
abhich:

If your laptop did not "recognize" your AMD card -- you would be seeing a black screen, and nothing else.  If you are seeing a desktop, then it IS recognizing the AMD card -- and has already installed the default Radeon drivers.

---

