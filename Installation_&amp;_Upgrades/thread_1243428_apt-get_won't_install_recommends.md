---
title: "apt-get won't install recommends"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by ShadowTek on 2009-08-18
I'm trying to use apt-get to install all the packages that go with the new kernel update, which are "recommended" packages, but apt-get keeps saying:
> The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-genericI had assumed that recommended packages were installed by default, but it seemed that this wasn't the case, so I tried using the --install-recommends option, but the result was the same.

What's the problem here?

---

### Post by Bachstelze on 2009-08-18
[http://ubuntuforums.org/showpost.php?p=7499891&postcount=11](http://ubuntuforums.org/showpost.php?p=7499891&postcount=11)

In a nutshell, run

```
sudo apt-get dist-upgrade
```

---

### Post by ShadowTek on 2009-08-18
That did it.
Thanks.

---

