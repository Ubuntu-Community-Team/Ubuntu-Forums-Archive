---
title: "Acer Aspire 5520-5716 Problems Booting"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by mespork on 2008-02-24
Hello,

I recently aquired an Acer Aspire 5520-5716. The problem that I having is that the laptop will not boot into Ubuntu after it is installed. It is almost like Ubuntu does not recognize the hard drive which it is installed on. It seems to be a problem with 2.6.22 Kernel as the laptop boots fine if I install Feisty (save the video). 

Does anyone have any ideas how to get around this issue?

Thanks,

David

---

### Post by LuisPT on 2008-02-26
Just do this:

In the Grub menu, before hit enter or the 10 seconds boot delay, hit the "e" key to edit the Ubuntu line boot and just add the following option: all_generic_ide.
Then press enter, then hit the "b" key to boot.

This is the most common problem issue with Ubuntu Acer laptops.

If this does'nt work, then you have a diferent problem.

---

