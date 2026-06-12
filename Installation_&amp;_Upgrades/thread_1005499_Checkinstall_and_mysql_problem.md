---
title: "Checkinstall and mysql problem"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by ShaolinF on 2008-12-08
Hi Guys

I am trying to install mysql community server 5.1.30 on my ubuntu 8.10 from source. I am using the latest version of checkinstall to simplify my uninstall of the server. So the following is what I do:

./configure --prefix=/to/my/dir
sudo make
sudo checkinstall

The problem is with the checkinstall. Everything works fine up untill then. I get an "**Installation failed. Aborting package creation**". Does anyone know where I am going wrong?

---

### Post by andrew.46 on 2008-12-11
Hi,

Can you give the section of checkinstall that fails? If it complains about files or directories that it cannot find there is a simple fix, run checkinstall as:

```
sudo checkinstall --fstrans=no
```

You can see a few more details about this bug here:

[http://ubuntuforums.org/showpost.php?p=6254063&postcount=59](http://ubuntuforums.org/showpost.php?p=6254063&postcount=59)

All the very best,

  Andrew

---

