---
title: "Kernel Confusion"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by Schrodinger's Hamster on 2006-10-18
Morning all.

I have installed Ubuntu 6.06 on my shiny new laptop (never been brave enough to do Linux before!) and have run into a few minor issues that I think are related to the kernel installed as default.

Laptop is a Dell 6400, 2Gb RAM, ATI Mobility Radeon 256Mb X1300 video card, T2400 Core Duo, 100Gb SATA hard drive.

Now, I found reference online to the dual core not being supported under the default kernel, and this article suggests running;

[CENTER]sudo apt-get install linux-686-smp[/CENTER]

This seemed to all go well, but the problem is I don't know how to check if this has actually done the trick and that both cores are being utilised :-? 


Next issue is that the screen resolution is stuck at a VESA like level.  Some online references seem to me to suggest that the kernel I installed above should support the ATI video, others that I need an entirely new kernel. There is also some reference made to being able to install kernel independent drivers from the ATI website, but after a few hours of trying this I was forced to give up to preserve my sanity ;) 

Is there a way of installing the latest kernel from the package manager bits of Ubuntu, or do I need to always use the apt-get bit?  Which Kernel should I be looking for anyway?

Sorry for the n00b first post - any and all help gratefully accepted :)

---

### Post by JaRoLLz on 2006-10-18
to see whether both cpu is used, type this

cat /proc/cpuinfo

you'll see that there are cpu0 and cpu1. Mine is T2300 Centrino Duo, and it works well!!!. You could also see system monitor, and you'll see that there are 2 processors

---

### Post by Schrodinger's Hamster on 2006-10-18
Ah - both cores are active!  They aren't doing much, but they are active ;)

---

### Post by Schrodinger's Hamster on 2006-10-18
And now I have managed to get the screen res right up to close what it does under Windows!

For anyone finding this thread I followed the instructions at;

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)

---

