---
title: "linux-headers uname -r couldn't be found"
date: 2008-08-20
forum: General Help
---

### Post by dorian821 on 2008-08-20
Im new to ubuntu, and linux in general. Ive been trying to install VMware, and in following a how to guide I enetered this command in the terminal "sudo apt-get install linux-headers-'uname -r' build-essential xinetd" and I always get the same response saying that uname-r cannot be found. any ideas?  can it be found in the synaptic manager?

---

### Post by kellemes on 2008-08-20
> **dorian821 said:**
> Im new to ubuntu, and linux in general. Ive been trying to install VMware, and in following a how to guide I enetered this command in the terminal "sudo apt-get install linux-headers-'uname -r' build-essential xinetd" and I always get the same response saying that uname-r cannot be found. any ideas?  can it be found in the synaptic manager?

It should be..
```
sudo apt-get install linux-headers-$(uname -r) build-essential xinetd
```
or enter your instructions 1 by 1 like so..
```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install build-essential
sudo apt-get install xinetd
```

---

### Post by amo-ej1 on 2008-08-20
the real problem you had is that you use a quote (') instead of a backtick (`) around the uname -r

```

edb@lapedb:~$ apt-cache search linux-headers-`uname -r`
linux-headers-2.6.24-19-generic - Linux kernel headers for version 2.6.24 on x86/x86_64


```

---

