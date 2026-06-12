---
title: "Error: Madwifi-NG"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by HumanPerson on 2007-08-06
I'm following this guide: [http://aircrack-ng.org/doku.php?id=madwifi-ng](http://aircrack-ng.org/doku.php?id=madwifi-ng)

After typeing "make", I get this errors:
```

./kernelversion.c:13:30: error: linux/utsrelease.h: No such file or directory
Makefile.inc:91: *** KERNELCONF: /lib/modules/2.6.20-16-386/build/.config does not exist.. Stop.

```

---

### Post by moore.bryan on 2007-08-06
[I]i solved this by expressly stating the kernel, as in:
```
sudo ./configure KERNELPATH=/usr/src/linux-headers-2.6.20-16-server
```
and doing that for each step...
[/I]

---

### Post by HumanPerson on 2007-08-07
```

sudo: ./configure: command not found

```
:?

---

### Post by moore.bryan on 2007-08-08
[I]before you "make," you needed to configure... didn't you type that?  oh, wait... i just checked-out the howto you're following and saw it doesn't have you compiling from source.  so, instead of specifying the kernel path in ./configure, just do it in the make and make install:
```
sudo make KERNELPATH=/usr/src/linux-headers-xxx
sudo make install KERNELPATH=/usr/src/linux-headers-xxx
```
[/I]

---

