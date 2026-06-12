---
title: "How do I install a gtk bug fix ??"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by selahlynch on 2008-12-16
In my installation of Ubuntu there is a problem resizing columns in the nautilus file browser. From what I can see, this is a result of a bug in gtk.  

See here:
[Bug 316087 – Resizing columns is chaotic]("http://bugzilla.gnome.org/show_bug.cgi?id=316087")

The bug has been fixed.  Now, how can I install this bug fix on my system? Can I do it without updating my entire operating system from 8.04 Hardy to 8.10 Intrepid?

I thought I could use Synaptic to install a new version of some package with gtk in the title but I'm not sure which package.

Thanks.

---

### Post by PmDematagoda on 2008-12-16
Unless Ubuntu gives you an update for the bug through the repositories, you would need to either upgrade to Intrepid, or obtain the source for the particular package/application, apply the patch, and then install it(getting rid of the old package/application is recommended).

---

### Post by selahlynch on 2008-12-16
What package would it be that is referenced in that bug report??  

I'm expecting a package named gtk+ to exist but I cannot see it when browsing package names in Synaptic.

---

