---
title: "Recompiling the original kernel"
date: 2008-10-04
forum: General Help
---

### Post by Dooley on 2008-10-04
Hey folks,

I'm using an acer aspire one and installed a new kernel with ubuntu 8.04 to speed things up. Sadly this kernel is a bit rubbish at everything else I need. I was wondering if its possible to recompile the original kernel that comes with ubuntu? Preferably using apt or if there's a handy guide I couldn't find with google.

Thanks in advance,
Dooley

---

### Post by iponeverything on 2008-10-04
Hi Dooley --

The magic google search words are --- drumroll......

ubuntu make-kpkg

good luck with the recompile.  I had to do a "strip -g" on all my modules though I am sure that there is someway to set it do that automatically.

---

### Post by lswb on 2008-10-04
The kernels are available in the repositories. If you don't need a custom kernel, it would likely be simpler and faster to just install the kernel you want. In synaptic start by searching for "linux-image" by name, or in a terminal 

apt-cache search "linux-image"

---

