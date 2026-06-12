---
title: "What is AMD Microcode Proprietary Driver For?"
date: 2015-07-30
forum: Hardware
---

### Post by lambdafox on 2015-07-30
After upgrading Xubuntu 14.10 amd64 to 15.04, I see a new item in the proprietary drivers list.  it is disabled by default and is called Processor microcode firmware for AMD CPUs from amd64-microcode??

I did not see this item listed in 14.10.

---

### Post by QIII on 2015-07-30
Hello!

Microcode (used by both Intel and AMD) is a subset of lower-level hardware instructions that implement some of the higher-level machine instructions in a number of types of processors.

Normally, linux-firmware handles microcode updates, so you don't have to worry about it much.  But things aren't always so simple, so I believe that driver facilitates the updates.

Would you please post back the results of 

```
dmesg | grep microcode
```

---

### Post by lambdafox on 2015-07-31
With the item disabled,

```
~$dmesg | grep microcode
[    0.915884] microcode: AMD CPU family 0xf not supported
```

With the item enabled it returns nothing.

While checking that, I noted that with the item disabled my startup items and desktop look more or less normal except conky.  With it enabled, my desktop icons do not appear and one of my startup items did not run.

I am guessing, disabled is the right choice??

---

### Post by Yellow Pasque on 2015-07-31
[https://bugs.launchpad.net/ubuntu/+source/amd64-microcode/+bug/1450188](https://bugs.launchpad.net/ubuntu/+source/amd64-microcode/+bug/1450188)

---

### Post by QIII on 2015-07-31
Nice catch, Temüjin. 

 lambdafox, you should add yourself to the list of affected users on that bug.

---

