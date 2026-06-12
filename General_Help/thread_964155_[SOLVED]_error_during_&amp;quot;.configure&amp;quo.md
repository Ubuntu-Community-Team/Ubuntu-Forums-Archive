---
title: "[SOLVED] error during &amp;quot;./configure&amp;quot; while compiling from source"
date: 2008-10-30
forum: General Help
---

### Post by eotakos on 2008-10-30
Hi! I was trying to install from source the keytouch app.
when i did ./configure like it's instructed in the readme file, i got this:

```
checking for libasound headers version >= 1.0.10... not present.
configure: error: Sufficiently new version of libasound not found.

```

so, i checked the synaptic, and the libasound2 package is installed, and the version is newer than the one required.

what is it that i don't get?

thanks!

---

### Post by Yellow Pasque on 2008-10-30
You need the -dev package if you're building from source.
```
sudo apt-get install libasound2-dev
```

---

### Post by eotakos on 2008-10-30
yeap! that did it! i didn't know that,

Thanks!

---

