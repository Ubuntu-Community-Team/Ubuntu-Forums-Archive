---
title: "Java Install error"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by cchir on 2009-07-31
Trying to install Java, but I am getting the following error, can some help?

./java_app_platform_sdk-5_07-linux-nojdk.bin
./java_app_platform_sdk-5_07-linux-nojdk.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by Partyboi2 on 2009-07-31
Hi, try installing the libstdc++5 package
```
sudo apt-get install libstdc++5
```

---

