---
title: "Removal of ies4linux"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by graceful1 on 2009-03-01
I installed ies4linux after reading about it, and now I am sorry I did that. How can I get this off my system? I am using Ubuntu 8.10. Thanks in advance

---

### Post by kestrel1 on 2009-03-01
How did you install it. Did you use a deb file or did you have to compile it yourself?

---

### Post by smo0th on 2009-03-01
I ran into the same case, I downloaded ies4linux from a tar file, decompressed it and ran the installer, after thar I had the ies4linux-2.9xx and the .ies4linux directories in my home folder, I searched the system for ies4linux remainders and all I found was the destop link and a couple of links inside a bin folder which was in my home folder, so basically what I did was to go to the terminal, cd to my home folder and type:

```
rm -R .ies4linux
rm -R ies4linux-2.99xx
rm -R bin
```

cheers,

---

### Post by graceful1 on 2009-03-02
> **kestrel1 said:**
> How did you install it. Did you use a deb file or did you have to compile it yourself?

I downloaded the tar.gz file that I believe came from the ies4linux web site.

---

