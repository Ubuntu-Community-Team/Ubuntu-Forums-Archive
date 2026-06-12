---
title: "which flashplayer plugin to use??"
date: 2008-09-13
forum: General Help
---

### Post by Dan78 on 2008-09-13
Pls help, i need to install a package that will play wmv mpeg etc. on web pages an so on i tried adobe 9 but say's that it's restricted, which is the best one for ubuntu 8.04 with pentium 1.5ghz 512mb .......pls help??

---

### Post by mb_webguy on 2008-09-13
The Flash plugin doesn't play media files, only embedded Flash.

For mpg, wmv, and other media files, you need the Totem (totem-mozilla) or MPlayer (mozilla-mplayer) plugins.  The Totem plugin should already be installed.

Open Firefox and type the following in the address bar, and copy and paste what you see in a post.```
about:plugins
```

---

### Post by mb_webguy on 2008-09-13
It you're trying to play YouTube videos, then that *is* Flash.  I suggest installing the Flash 10 plugin from the backports repository.  For instructions on how to do this, check the link in my signature.

EDIT:  By the way, I don't think "restricted" in this case means what you think it means.  It simply means that Ubuntu can't put this software in the default installation due to licensing or copyright issues.

---

### Post by Pharohs on 2008-09-13
I ended up installing all three options I was given.  I have no idea which one is working, but, I can see the Flash videos now.

---

