---
title: "dkms build can't find config.mk but it is there"
date: 2014-12-01
forum: Hardware
---

### Post by jbdough on 2014-12-01
DKMS make.log for rt5592sta-1.0 for kernel 3.13.0-40-generic (x86_64)
Mon Dec  1 19:37:41 PST 2014
make: Entering directory `/var/lib/dkms/rt5592sta/1.0/build/os/linux'
Makefile:1: /os/linux/config.mk: No such file or directory
make: *** No rule to make target `/os/linux/config.mk'.  Stop.
make: Leaving directory `/var/lib/dkms/rt5592sta/1.0/build/os/linux'

john@asus:~/N600PCE_driver/dkms$ ls -l  /var/lib/dkms/rt5592sta/1.0/build/os/linux/config.mk
-rw-r--r-- 1 root root 32437 Dec  1 19:37 /var/lib/dkms/rt5592sta/1.0/build/os/linux/config.mk

This has to be too obvious for me to see it.

I just couldn't stand the success I enjoyed [getting a Ralink controller to work]("http://ubuntuforums.org/showthread.php?t=2251150&p=13177936#post13177936") - had to try dkms

---

### Post by steeldriver on 2014-12-02
in
```

make: *** No rule to make target `/os/linux/config.mk'.  Stop.

```
the target `/os/linux/config.mk' is an absolute path - that's not the same thing as
```

/var/lib/dkms/rt5592sta/1.0/build/os/linux/config.mk

```
or
```

**.**/config.mk

```

---

### Post by jbdough on 2014-12-02
thanks steeldriver.  

I got it to build, but the resultant output byte count is different for  rt5592sta* files than the ones already modprobed that are making this connection possible.
For the few applications I occasionally compile from source I think I'll just stick with make clean->make->make install if they break on a kernel update.

---

