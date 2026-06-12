---
title: "HELP High Memory Support"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by morfyng on 2006-11-02
Hi everyone,

I'm compiling the kernel 2.6.16 on Ubuntu/Edgy for the first time and I have a "doubt" at the section below:

**[SIZE="2"]High Memory Support[/SIZE]**
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set

CONFIG_PAGE_OFFSET=0xC0000000
CONFIG_HIGHMEM=y

**[SIZE="2"]User address space size[/SIZE]**
# CONFIG_05GB is not set
CONFIG_1GB=y
# CONFIG_2GB is not set
# CONFIG_3GB is not set

I have 2GB of physical ram on my laptop therefore I understood that the CONFIG_HIGHMEM4G=y is an obliged choice but I'm not sure about CONFIG_1GB=y parameter.

Please hel me

---

### Post by po0f on 2006-11-02
morfyng,

I think those options are how the memory will be divided.  With the CONFIG_1GB option set, memory will be divided 1G for kernel, 1G for userspace.

I'm not too sure, though;  in the past when configuring kernels, I left options I wasn't sure about at their defaults, so I think you'll be fine with the defaults.

---

### Post by morfyng on 2006-11-03
Hello, po0f, and thanks for your answer

should be how do you've said, also whether I've found an [article ]("http://kerneltrap.org/node/2450")about the High memory support where the relation between the Kernel virtual space and the User-space virtual space seems not be 1:1 :-? 

bah!!! however I use the default option ;) Bye

---

