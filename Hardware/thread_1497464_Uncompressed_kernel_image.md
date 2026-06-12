---
title: "Uncompressed kernel image"
date: 2010-05-30
forum: Hardware
---

### Post by GigaVolt on 2010-05-30
Hi,

Anybody been able to decompressed kernel to speed loading?

I tested this:
root@income:/boot# file vmlinuz-2.6.32-22-generic
vmlinuz-2.6.32-22-generic: Linux kernel x86 boot executable bzImage, version 2.6.32-22-generic (buildd@rothe, RO-rootFS, root_dev 0x801, swap_dev 0x3, Normal VGA
root@income:/boot# bunzip2 vmlinuz-2.6.32-22-generic
bunzip2: Can't guess original name for vmlinuz-2.6.32-22-generic -- using vmlinuz-2.6.32-22-generic.out
bunzip2: vmlinuz-2.6.32-22-generic is not a bzip2 file.
root@income:/boot#

---

### Post by Zemblan on 2010-05-30
I don't think the kernel is compressed simply with bzip2, it's somewhat more complicated to create the bzImage and has various components.
See here: [http://en.wikipedia.org/wiki/Vmlinux](http://en.wikipedia.org/wiki/Vmlinux)

There's a link on that page to a script for unpacking the kernel. I'm not sure it's really worth the effort though, probably a very small speed-up in boot times.

---

### Post by sdennie on 2010-05-30
> **Zemblan said:**
> I'm not sure it's really worth the effort though, probably a very small speed-up in boot times.

It may even be a wash or speed decrease depending on the machine.  If the compression level is good it's entirely possibly that it's faster to read and uncompress a very small file into memory than it is to read a much larger file(s) into memory.

---

