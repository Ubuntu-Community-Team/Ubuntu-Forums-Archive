---
title: "How to check installed files from the terminal?"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Metallion on 2009-02-13
You know how when you go into synaptic, you can check exactly which files a package has installed on your computer? I'm wondering how it's possible to see that from the terminal. I know I could just open synaptic and have a look there but I'm rather fond of my terminal. :)

Thanks

---

### Post by cdtech on 2009-02-13
This uses the "dpkg - package manager". Use the command:
```
dpkg -L wireless-tools
```
to view installed files. Use:
```
dpkg -s wireless-tools
```
To see the status and dependencies of the installed package.
```

dpkg -l | grep ii
```
Will give you a list of installed packages.

See "man dpkg" for more information......

---

