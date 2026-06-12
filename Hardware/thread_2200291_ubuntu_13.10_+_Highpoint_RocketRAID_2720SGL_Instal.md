---
title: "ubuntu 13.10 + Highpoint RocketRAID 2720SGL Installation help"
date: 2014-01-18
forum: Hardware
---

### Post by 74kumi on 2014-01-18
Hi to get straight to the point I'm trying to install the driver/module for this raid card and so far it gives me nothing but errors there generic ./install file for ubuntu doesn't work, 272x_1x doesn't show up in modprobe or lsmod even after a reboot as it asks. Ive tryed compileing the drivers from the source file they provide and that throws errors:
```
/rr272x_1x-linux-src-v1.5/product/rr272x/linux$ make installmake[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/os_linux.o
  CC [M]  /home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/osm_linux.o
/home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/osm_linux.c:2126:2: error: unknown field âproc_infoâ specified in initializer
  proc_info:               hpt_proc_info26,
  ^
/home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/osm_linux.c:2126:2: warning: initialization from incompatible pointer type [enabled by default]
/home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/osm_linux.c:2126:2: warning: (near initialization for âdriver_template.proc_dirâ) [enabled by default]
make[2]: *** [/home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build/osm_linux.o] Error 1
make[1]: *** [_module_/home/takumi/rr272x_1x-linux-src-v1.5/product/rr272x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [rr272x_1x.ko] Error 2



```

quick breakdown of my specks:
ubuntu 13.10 
rocketRaid 2720sgl
amd athlon x2 4200
2x1tb 2x2tb 2x3tb 1x500gig

Goal
working driver so HW raid can make 3 raid1s 

If you need any more info or logs just let me know i will be happy to post them I just want to get this working

---

### Post by 74kumi on 2014-01-18
solution -> [http://ubuntuforums.org/showthread.php?t=1899544&page=3](http://ubuntuforums.org/showthread.php?t=1899544&page=3)

---

### Post by JohnAreBee on 2014-03-06
UPDATE: New official drivers have been released checkout: [http://ubuntuforums.org/showthread.php?t=2214489&p=12974319#post12974319](http://ubuntuforums.org/showthread.php?t=2214489&p=12974319#post12974319)

---

