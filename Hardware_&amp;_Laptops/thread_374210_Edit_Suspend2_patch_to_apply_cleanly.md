---
title: "Edit Suspend2 patch to apply cleanly"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2007-03-02
Hello,

  Trying to install suspend2 for dapper (2.6.15-28-686) but always get a error that my patch won't apply cleanly.   This is not as surprise according to the Software Suspend2 HOWTO:

[B][I] Once you have succeeded in compiling your kernel, you can apply the Suspend2 patches against your source tree. This is most easily done using a command along the lines of...

cd /usr/src/linux (the root directory of your tree)
bzcat /path/to/patch | patch -p1

If the kernel versions match, then no rejects or offsets should occur. If your kernel is not the vanilla one from kernel.org, you will have to apply these patches manually and edit some of the rejected hunks.[/I][/B]

I'm using the current running ubuntu kernel (2.6.15-28-686), not a vanilla kernel from kernel.org.

1)  What are the differences between the ubuntu kernel and a vanilla kernel?

or

2) How do I edit (customise) the patches so that they'll apply cleanly to my kernel?

Thanks
- CH

---

