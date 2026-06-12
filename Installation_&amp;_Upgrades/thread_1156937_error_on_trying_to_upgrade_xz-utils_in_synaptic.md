---
title: "error on trying to upgrade xz-utils in synaptic"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Packrat73 on 2009-05-12
xz-utils replaces lzma so when I try to upgrade it I get.
E: /var/cache/apt/archives/xz-utils_4.999.8beta-1~jaunty1_i386.deb: trying to overwrite `/usr/bin/unlzma', which is also in package lzma

but if I uninstall lzma it also uninstalls a ton of applications that depend on lzma. I dont want to kill something else to upgrade, How do I upgrade to xz-utils from lzma without having to uninstall a bunch of important stuff? Thanks.

---

### Post by Partyboi2 on 2009-05-12
Hi, you could use the force overwrite option from a terminal
```
cd /var/cache/apt/archives
```

```
sudo dpkg --force-overwrite --install xz-utils_4.999.8beta-1~jaunty1_i386.deb
```

---

### Post by Packrat73 on 2009-05-12
I think that did the trick. Thanks.

---

