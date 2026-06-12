---
title: "Dell Inspiron 1525 wireless problems"
date: 2008-10-04
forum: Hardware
---

### Post by beno1990 on 2008-10-04
I have a Dell Inspiron 1525 laptop which was shipped with Ubuntu. However, I ended up having to reinstall the OS and since then, my wireless hasn't worked at all, and the OS isn't even picking up the existence of the device.

I get the following on the terminal:

```
$ lspci | grep -i network
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

If anyone could help me with this I'd greatly appreciate it.

---

### Post by beno1990 on 2008-10-05
Ok, I got it. But I've seen a few similar problems around here so I'll explain how I fixed it.

I just needed to install the Hardy Backports kernel modules, but because I couldn't connect from the internet I had to download it manually from another computer and transfer the package over across a pen drive.

If you need this package, chances are you're working from a fresh CD install with the kernel version on the CD, so you should use this package:

[http://packages.ubuntu.com/hardy-updates/linux-backports-modules-2.6.24-19-generic]("http://packages.ubuntu.com/hardy-updates/linux-backports-modules-2.6.24-19-generic")

Don't forget to enable the backports in your software sources after though, or any kernel updates won't be compatible with that version of the modules.

---

### Post by untjake on 2008-12-15
Could you elaborate on how to install this backport? I've download the file you linked to and I get "Error: Dependency is not satisfiable: linux-image-2.6.24-19-generic" when trying to install it.

Is this another file I have to download in order to get this working?

---

