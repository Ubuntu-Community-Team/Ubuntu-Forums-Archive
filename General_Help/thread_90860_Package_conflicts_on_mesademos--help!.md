---
title: "Package conflicts on mesademos--help!"
date: 2005-11-15
forum: General Help
---

### Post by grendel_khan on 2005-11-15
I wanted to try out some of the Mesa demos on a recent 5.10 install. There's a package, mesademos, for them. So, I did an ```
$ sudo apt-get install mesademos -s
``` and it suggested packages "mesag-dev libgl-dev glutg3-dev". The first two resolve to libgl1-mesa-dev. If I try to install that, I get ```
The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.3.2-0ubuntu6) but 6.3.2-0ubuntu6breezy1 is to be installed
E: Broken packages
```

If I try to downgrade (sudo apt-get install libgl1-mesa=6.3.2-0ubuntu6 -s), it threatens to uninstall ubuntu-desktop and x-window-system-core. Not downgraded, but removed, which I don't think I want. Oddly enough, the version of libgl1-mesa on packages.ubuntu.com is [6.3.2-0ubuntu6](http://packages.ubuntu.com/breezy/libs/libgl1-mesa).

I just want to try out the Mesa demos. Where did I go wrong here?

---

