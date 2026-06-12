---
title: "xbox360 wireless controller issues"
date: 2012-10-10
forum: Hardware
---

### Post by matthill11 on 2012-10-10
I am trying to follow the directions found [here ]("https://help.ubuntu.com/community/Xbox360Controller")and when I run the Makefile i get 
```
MatthewLT ~ # cd xpad
MatthewLT xpad # make
make modules -C /usr/src/linux-headers-3.2.0-23-generic SUBDIRS=/root/xpad
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /root/xpad/xpad.o
/root/xpad/xpad.c:66:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/root/xpad/xpad.o] Error 1
make[1]: *** [_module_/root/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2
MatthewLT xpad # 
```I have no idea what I am doing wrong any help would be greatly appreciated

---

### Post by Bucky Ball on 2012-10-10
Did you, "Make sure the tabs under "all:" and "install:" remain[ed] intact." when you put the data into the makefile? Maybe check ...


```
all:         
               $(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)  

install:         
               cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

---

### Post by matthill11 on 2012-10-10
i typed in "all:[enter][tab]$(MAKE) modules -C $(KERNEL_PATH) SUBDIRS=$(shell pwd)[enter][enter]install:[enter][tab]cp -f xpad.ko" ect...

---

### Post by Bucky Ball on 2012-10-10
I would just empty that file and paste in what they have on the page and try again. Then you will know you have it exactly.

---

### Post by matthill11 on 2012-10-10
i tried that too with the same results

---

