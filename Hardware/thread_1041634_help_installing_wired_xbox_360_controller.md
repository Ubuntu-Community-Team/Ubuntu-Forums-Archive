---
title: "help installing wired xbox 360 controller"
date: 2009-01-16
forum: Hardware
---

### Post by c/Kr3t on 2009-01-16
so i'm following the guide from [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) and i'm stuck.

after i make the Makefile i get this when i 'make'

```
make modules -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/home/danny/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/danny/xpad/xpad.o
/home/danny/xpad/xpad.c: In function ‘xpad_open’:
/home/danny/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/danny/xpad/xpad.c: In function ‘xpad_close’:
/home/danny/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/danny/xpad/xpad.c: In function ‘xpad_probe’:
/home/danny/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/danny/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/danny/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/danny/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

```

any suggestions on how to fix this?

---

### Post by mole2006 on 2009-01-18
> **c/Kr3t said:**
> so i'm following the guide from [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) and i'm stuck.

after i make the Makefile i get this when i 'make'

```
make modules -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/home/danny/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/danny/xpad/xpad.o
/home/danny/xpad/xpad.c: In function ‘xpad_open’:
/home/danny/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/danny/xpad/xpad.c: In function ‘xpad_close’:
/home/danny/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/danny/xpad/xpad.c: In function ‘xpad_probe’:
/home/danny/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/danny/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/danny/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/danny/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

```

any suggestions on how to fix this?

Same error, any help?

---

### Post by mobius1 on 2009-01-26
Make that three...

---

### Post by c/Kr3t on 2009-01-26
all the guides i find all say the same thing

---

### Post by ASchweitzer on 2009-01-27
Just a stab in the dark here, but try moving your source code to the desktop and running make from there. It is beyond my knowledge *why*, but I've had situations where code refused to make properly in my home directory, yet worked fine from a folder on the desktop.

---

### Post by NaturalCauzes on 2009-02-23
tried from desktop...same issue....maybe the new kernel?

---

### Post by c/Kr3t on 2009-03-02
bump

---

