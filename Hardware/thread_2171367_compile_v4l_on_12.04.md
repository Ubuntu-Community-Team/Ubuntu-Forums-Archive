---
title: "compile v4l on 12.04"
date: 2013-08-30
forum: Hardware
---

### Post by shlomicthailand on 2013-08-30
Hi guys 

i'm new here , and have some experience with ubuntu but not a master.
i have upgraded my ubuntu from 10.04 -> 12.04 

i have a DVB-T dongle i'm trying to compile the V4L for it - according to this guide [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
i also installed linux-sources-3.2.0-52
but there is a compilel error i'm not able to find answer to 

here it is 



  CC [M]  /home/shlomic/v4l/media_build/v4l/v4l2-clk.o
  CC [M]  /home/shlomic/v4l/media_build/v4l/v4l2-async.o
  CC [M]  /home/shlomic/v4l/media_build/v4l/v4l2-of.o
/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_parse_csi_bus':
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:38:4: error: implicit declaration of function 'of_prop_next_u32' [-Werror=implicit-function-declaration]
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:38:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_get_next_endpoint':
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:176:3: error: implicit declaration of function 'of_get_child_by_name' [-Werror=implicit-function-declaration]
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:176:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:180:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_get_remote_port_parent':
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:238:2: warning: passing argument 1 of 'of_parse_phandle' discards 'const' qualifier from pointer target type [enabled by default]
include/linux/of.h:230:28: note: expected 'struct device_node *' but argument is of type 'const struct device_node *'
/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_get_remote_port':
/home/shlomic/v4l/media_build/v4l/v4l2-of.c:262:2: warning: passing argument 1 of 'of_parse_phandle' discards 'const' qualifier from pointer target type [enabled by default]
include/linux/of.h:230:28: note: expected 'struct device_node *' but argument is of type 'const struct device_node *'
cc1: some warnings being treated as errors
make[3]: *** [/home/shlomic/v4l/media_build/v4l/v4l2-of.o] Error 1
make[2]: *** [_module_/home/shlomic/v4l/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/shlomic/v4l/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 454.
shlomic@shlomic-ubuntu:~/v4l/media_build$

---

### Post by coffeecat on 2013-08-31
Duplicate here:

[http://ubuntuforums.org/showthread.php?t=2171567](http://ubuntuforums.org/showthread.php?t=2171567)

Please do not post duplicate threads.

Thread closed.

---

