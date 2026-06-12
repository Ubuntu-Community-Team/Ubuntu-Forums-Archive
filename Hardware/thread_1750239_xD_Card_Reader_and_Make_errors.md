---
title: "xD Card Reader and Make errors"
date: 2011-05-05
forum: Hardware
---

### Post by wizard710 on 2011-05-05
I'm trying to get my Ricoh Card reader to work and came across this

[http://gitorious.org/ricoh-kernel](http://gitorious.org/ricoh-kernel)

I've downloaded a clone and in the xd folder I have run make and it then just spits out this

```
chris@Chris-PC:~/ricoh-kernel/xd$ make
make -C /lib/modules/2.6.38-8-generic/build M=/home/chris/ricoh-kernel/xd
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/chris/ricoh-kernel/xd/nand/built-in.o
  CC [M]  /home/chris/ricoh-kernel/xd/nand/nand_base.o
  CC [M]  /home/chris/ricoh-kernel/xd/nand/nand_bbt.o
  LD [M]  /home/chris/ricoh-kernel/xd/nand/nand.o
  CC [M]  /home/chris/ricoh-kernel/xd/nand/nand_ecc.o
  CC [M]  /home/chris/ricoh-kernel/xd/nand/nand_ids.o
  CC [M]  /home/chris/ricoh-kernel/xd/nand/sm_common.o
  CC [M]  /home/chris/ricoh-kernel/xd/nand/r852.o
/home/chris/ricoh-kernel/xd/nand/r852.c: In function ‘r852_probe’:
/home/chris/ricoh-kernel/xd/nand/r852.c:946:2: error: implicit declaration of function ‘create_freezeable_workqueue’
/home/chris/ricoh-kernel/xd/nand/r852.c:946:22: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/chris/ricoh-kernel/xd/nand/r852.o] Error 1
make[2]: *** [/home/chris/ricoh-kernel/xd/nand] Error 2
make[1]: *** [_module_/home/chris/ricoh-kernel/xd] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [build] Error 2

```

What is going wrong.

Sorry I'm quite newbish.

---

