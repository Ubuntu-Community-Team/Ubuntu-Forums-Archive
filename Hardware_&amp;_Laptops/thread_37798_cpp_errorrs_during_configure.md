---
title: "cpp errorrs during configure"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by ::DoGG:: on 2005-05-28
```
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```

i got this while try to compile audioscrobbler xmms plugin. I got cpp installed, /lib/cpp exists. Any clues ?

---

### Post by Xian on 2005-05-28
Have you installed the build essentials meta-package?

```
$ sudo apt-get install build-essential
```

---

### Post by ::DoGG:: on 2005-05-28
Now i have :D Thanks a lot!

---

