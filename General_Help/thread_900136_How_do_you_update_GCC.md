---
title: "How do you update GCC?"
date: 2008-08-25
forum: General Help
---

### Post by blah5754745 on 2008-08-25
I get this error when installing X-Fi drivers
```
checking for kernel version... 2.6.24-21-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

```

was wondering if updating gcc would solve my issue..
and how would i go about doing so?

---

### Post by -Zeus- on 2008-08-25
try running this;

```
sudo apt-get install gcc linux-headers-generic
```

---

### Post by blah5754745 on 2008-08-25
ty, but that didn't do it for the drivers/already was up to date

hmmm

---

