---
title: "Possible to use a kernel from breezy in hoary?"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by jimbot on 2005-09-08
Hi,

I have an onboard soundcard which is only supported by kernel 2.6.12.5+. It therefore doesn't work with a standard install of Hoary, but since Breezy uses/will use a later kernel, could I install a kernel package from Breezy? Is it just a matter of changing "hoary" in sources.list to "breezy"? And, umm, anyone know what kernel breezy currently uses? :)

Thanks,
Jim

---

### Post by tseliot on 2005-09-08
[QUOTE=jimbot] Is it just a matter of changing "hoary" in sources.list to "breezy"?
[/QUOTE]
Yes it is (but remember to set it back to hoary after you install the kernel and kernel headers, otherwise you might screw up your system if you do an upgrade of the full system as Breezy is not stable yet).

I think is 2.6.12-8 but maybe I'm wrong. By the way I used a Breezy kernel and it worked fine. Keep in mind that if you have to install nvidia drivers you could have problems unless you tell the installer to use the right gcc (I made a guide about that if you need it)

Have fun!

---

