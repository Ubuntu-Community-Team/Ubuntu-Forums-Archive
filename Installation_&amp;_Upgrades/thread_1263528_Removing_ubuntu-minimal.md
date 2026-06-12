---
title: "Removing ubuntu-minimal"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by bfrosty on 2009-09-11
Can anybody tell me whether it is safe to hit 'Y' here:

```
apt-get root@XXX:~# apt-get remove vim-tiny

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-minimal vim-tiny
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
After this operation, 799kB disk space will be freed.
Do you want to continue [Y/n]?
```

Removing ubuntu-minimal? I looked this up in the repositories and this package looks kinda important. Can I prevent the apt-get utility from removing dependencies?

Much appreciated.

---

### Post by cak3 on 2009-09-11
Packages like ubuntu-minimal don't add much themselves, but rather depend on a bunch of other things, so installing the one packages forces all the dependencies to be installed. So, if you really want to get rid of vim-tiny (which is, needless to say, very small) you should be safe.

That being said, why would you want to get rid of it anyway? It takes up almost no space and is included in the ubuntu-minimal because it provides a powerful text editor in any environment.

But, anyway, the reason it is removing ubuntu-minimal is because ubuntu-minimal depends on vim-tiny, so it can't be instlled without it. That won't remove all the other packages that were installed with ubuntu-minimal though. I would still keep it, were I you.

A word of caution. I am not 100% certain that ubuntu-minimal does not do anything itself, though you would likely be able to reinstall it if it broke anything.

---

### Post by bfrosty on 2009-09-11
Thanks cak,

I wanted to install straight vim as I wanted to use the nerdtree plugin.

---

### Post by cak3 on 2009-09-11
ah yea. Just install vim on top of it. (or vim-full, which installs a couple other packages). Thats actually one of the first things I install on a new system. There isn't any kind of conflict.

---

