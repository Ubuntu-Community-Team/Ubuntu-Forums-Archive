---
title: "Problems in installation of nfs-utils-1.1.3"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by michez on 2009-07-23
Hi,

I am trying to compile and install nfs-utils-1.1.3. When typing ./configure, it says:

configure: error: Unable to locate information required to use librpcsecgss.  If you have pkgconfig installed, you might try setting environment variable PKG_CONFIG_PATH to /usr/local/lib/pkgconfig

I have the file pkg-config installed (is it the same as pkgconfig?). But after copying it to /usr/local/lib/, and setting the variable PKG_CONFIG_PATH to point to it, I get the same configure error.

Please help,
Thanks,
    Michael.

---

### Post by starcannon on 2009-07-23
I'm not sure what your project is, but perhaps the path of least resistance is:
```

sudo apt-get install ntfs-config ntfsprogs

```If that does not get you where your headed, then soldier on; perhaps try using Synaptic Package Manager to locate any of the possible missing packages that the compiler error complaint mentions, viz. pkgconfig

Also don't forget when you want to compile from source, a bare minimum is:
```

sudo apt-get install build-essential

```GL and HF

---

### Post by michez on 2009-07-23
Thank you very much for your answer.

Michael.

---

