---
title: "Installing wifi drivers"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by jwegan on 2005-09-21
I'm a linux newbie, having some trouble

I'm following directions here on installing wifi drivers for my card, however I'm getting errors.

I got the source code for linux 2.6.10 through apt-get and untared it. (I'm currently on kernel 2.6.10-5-686 though)
and i also got the linux-headers-2.6.10-5-686 files.

When I tried doing ./Configure with the drivers it said that my /sbin/ksyms was broken and it tried finding a /proc/ksyms but that didn't work.
I then copied the Module.symvers from my linux-headers directory to my linux-source directory and then configure runs fine. However when I do ./Build i get a lot of errors. (Check the build.txt attatchment for the build output)

Can anyone take a look at this and tell me exactly what I need to do step by step? I am completely lost

---

### Post by jwegan on 2005-09-23
bump, 

Can someone tell me how to get the source code for 2.6.10-5-686? I think the reason the build fails is because its using the wrong source or something.

---

