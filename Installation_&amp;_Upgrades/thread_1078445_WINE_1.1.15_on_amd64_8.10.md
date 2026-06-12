---
title: "WINE 1.1.15 on amd64 8.10"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by otheracco on 2009-02-23
OK, I compiled Wine 32 bit (because I can't find 1.1.15 beta in amd64) following [these]("http://wiki.winehq.org/WineOn64bit") directions.

It took about 40 minutes to complete, but when it was finished I type in 'wine' in a terminal, hit enter, and it can't find it.

Am I missing something like a symlink?

---

### Post by taurus on 2009-02-23
Are you in the directory where you just built wine?  You need to include a ./ in front of the name since that directory is not in your path.

```
./wine
```

---

### Post by whoop on 2009-02-23
I used this tutorial to compile/install wine 1.1.15 on jaunty; maybe you mist something. Check it out:
[http://tuxarena.blogspot.com/2008/09/how-to-compile-and-install-wine-114-in.html](http://tuxarena.blogspot.com/2008/09/how-to-compile-and-install-wine-114-in.html)

---

