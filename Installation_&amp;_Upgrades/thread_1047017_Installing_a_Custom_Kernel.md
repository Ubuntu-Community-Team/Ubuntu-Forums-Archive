---
title: "Installing a Custom Kernel"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by beastrace91 on 2009-01-22
So I followed this guide found here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I then installed this patch: ```
diff -Naur arch/x86/pci/i386.c arch/x86/pci/i386.c
--- arch/x86/pci/i386.c	2008-06-03 20:24:26.000000000 -0400
+++ arch/x86/pci/i386.c	2008-06-03 20:25:40.000000000 -0400
@@ -122,6 +122,10 @@
 				r = &dev->resource[idx];
 				if (!r->flags)
 					continue;
+				if ((r->start == 0xbdf00000) && (r->end == 0xddefffff)) {
+					r->start = 0xc0000000;
+					r->end = 0xe0000000;
+				}
 				pr = pci_find_parent_resource(dev, r);
 				if (!r->start || !pr ||
 				    request_resource(pr, r) < 0) {

```

Using: ```
sudo patch -p 0 < NVRM_512M_fix.txt
``` and it said it patched just fine...

I then compiled the Kernel and currently have 6 different .deb files in my home dir. that it created... several of them say they are already installed how ever, should I tell it to reinstall them? I don't want to mess up my install but I really want to get this patch working so I can use my extra ram. Any input is greatly welcome...

Thanks,
~Jeff

---

### Post by lemming465 on 2009-01-25
.deb packages can usually be installed with *dpkg -i*.  If you are getting messages about them already being installed, and you want to live dangerously, you could start adding things like *--force=overwrite*.  See *man dpkg* for more options.

Um, is it actually necessary to recompile the kernel to get your memory recognized?  You could try booting the regular kernel with *mem=2G* if it's not being recognized. (See Documentation/kernel-parameters.txt for the particulars). 32 bit desktop kernels are only compiled by default for 4GiB by Ubuntu, so if you ever installed more than that you'd need to either use a 64-bit install, a server kernel, or compile a desktop kernel with different options.

---

### Post by beastrace91 on 2009-01-26
The recompile was necessary, search around online for Asus G1Sn 3+ gigs of ram + linux, I have recompiled and installed it now though and it is all working :)

~Jeff

---

