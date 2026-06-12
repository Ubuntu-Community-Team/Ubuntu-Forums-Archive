---
title: "1GB Ram support"
date: 2004-10-15
forum: Hardware &amp; Laptops
---

### Post by tophfisher on 2004-10-15
Hello! 

I my laptop has 1GB of Ram, but ubuntu only sees 906MB. With Gentoo I had to build my own Kernels, and turned on large memory support... Is there a way to do this in Ubuntu? Do I need to load the SMP kernel?

Thanks!
-Chris

---

### Post by Markus78 on 2004-10-19
hi!

the kernel doesn't support 1gb ram because it is made for i386. try to install the i686 (is available at main i think (or contrib)) kernel and everything should work fine. 

hope it works

---

### Post by tophfisher on 2004-10-19
That did the trick, thanks! 

If any ubuntu devs are reading, I do not know if you guys roll your Kernels, or if these are Debians, but one neat patch would be the support for 1GB of RAM with out having to turn on large memory support. And you folks might already be doing that.

Thanks again!

[quote=Markus78]hi!

the kernel doesn't support 1gb ram because it is made for i386. try to install the i686 (is available at main i think (or contrib)) kernel and everything should work fine. 

hope it works[/quote]

---

