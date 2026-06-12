---
title: "Can I install a kernel module under a different name?"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by jb64 on 2009-05-04
I'd like to have my Atheros ath9k wireless driver compiled with some custom patches (for packet injection, among other things).  So I've downloaded the source tarball for linux's wireless drivers from [here]("http://linuxwireless.org/en/users/Download"), and I can install them with
```

make && sudo make install

```
But the problem is that they seem very spotty - i.e. I get disconnected from my AP a lot.  So what I'd like to do, if possible, is compile and install the ath9k driver under a different name, so I can use the ath9k driver provided by Ubuntu for normal things like web browsing, then unload it and load the custom ath9k driver for things like aircrack.  Is there a way to do this?

---

