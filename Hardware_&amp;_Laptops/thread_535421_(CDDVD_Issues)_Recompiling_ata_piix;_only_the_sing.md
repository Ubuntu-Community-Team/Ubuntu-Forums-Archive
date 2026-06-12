---
title: "(CD/DVD Issues) Recompiling ata_piix; only the single module"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by TradiZ on 2007-08-26
Hi,

I need some help understanding how to compile a single module in the Ubuntu Fiesty kernel 2.6.20-16-generic.

I have a very new computer with Intel Santa Rosa (ICH8 ) and my Cdrom is not there due to this Bug:

[http://bugzilla.kernel.org/show_bug.cgi?id=8835](http://bugzilla.kernel.org/show_bug.cgi?id=8835)

I installed Kernel 2.6.22.3 and the patch is included in that kernel and Cdrom works. Now I am back (clean install) to 2.6.20-16-generic and would like to recompile only the ata_piix module with the patch from the above link.

What do I need to install, and how is the procedure done in this case?

I have installed build-essential, linux-headers-generic, linux-image-generic, linux-restricted-modules-generic, linux-source (not unpacked yet)

uname -a = 2.6.20-16-generic

Thanks in advance,

Tradiz

---

### Post by ddrichardson on 2007-08-27
Does [this]("http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html") help?

---

### Post by TradiZ on 2007-08-27
Thanks,

Exactly what I needed.

TradiZ

---

