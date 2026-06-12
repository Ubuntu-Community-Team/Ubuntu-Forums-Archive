---
title: "Installing aircrack-ng into ubuntu 8.04 error"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by akekis on 2009-02-17
Dear guys,
I have recently encountered a problem while installing aircrack-ng through a guide here: [http://www.aircrack-ng.org/doku.php?id=newbie_guide](http://www.aircrack-ng.org/doku.php?id=newbie_guide).

1)tar xfz aircrack-ng-1.0-rc1.tar.gz - no problem at all
2)cd aircrack-ng-1.0-rc1
3)make- this is where i encounter errors:

fabian@fabian-laptop:~$ tar xfz aircrack-ng-1.0-rc1.tar.gz
fabian@fabian-laptop:~$ cd aircrack-ng-1.0-rc1
fabian@fabian-laptop:~/aircrack-ng-1.0-rc1$ make
make -C src all
make[1]: Entering directory `/home/fabian/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/fabian/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/fabian/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
osdep.c:21:20: error: stdlib.h: No such file or directory
osdep.c:22:20: error: assert.h: No such file or directory
osdep.c:23:20: error: string.h: No such file or directory
In file included from osdep.c:25:
osdep.h:11:24: error: netinet/in.h: No such file or directory
osdep.h:12:20: error: stdint.h: No such file or directory
In file included from osdep.c:25:
osdep.h:26: error: expected specifier-qualifier-list before ‘uint64_t’
cc1: warnings being treated as errors
osdep.h:106: warning: ‘struct in_addr’ declared inside parameter list
osdep.h:106: warning: its scope is only this definition or declaration, which is probably not what you want
osdep.h:127: warning: ‘struct in_addr’ declared inside parameter list
In file included from osdep.c:26:
network.h:11:22: error: inttypes.h: No such file or directory
network.h:12:23: error: sys/types.h: No such file or directory
In file included from osdep.c:26:
network.h:30: error: expected specifier-qualifier-list before ‘uint8_t’
osdep.c: In function ‘wi_read’:
osdep.c:30: warning: implicit declaration of function ‘assert’
osdep.c: In function ‘wi_alloc’:
osdep.c:94: warning: implicit declaration of function ‘malloc’
osdep.c:94: warning: incompatible implicit declaration of built-in function ‘malloc’
osdep.c:96: error: ‘NULL’ undeclared (first use in this function)
osdep.c:96: error: (Each undeclared identifier is reported only once
osdep.c:96: error: for each function it appears in.)
osdep.c:97: warning: implicit declaration of function ‘memset’
osdep.c:97: warning: incompatible implicit declaration of built-in function ‘memset’
osdep.c:101: warning: implicit declaration of function ‘free’
osdep.c: In function ‘wi_open’:
osdep.c:148: error: ‘NULL’ undeclared (first use in this function)
osdep.c:150: warning: implicit declaration of function ‘strncpy’
osdep.c:150: warning: incompatible implicit declaration of built-in function ‘strncpy’
osdep.c: At top level:
osdep.c:199: warning: ‘struct in_addr’ declared inside parameter list
osdep.c:200: error: conflicting types for ‘ti_set_ip’
osdep.h:127: error: previous declaration of ‘ti_set_ip’ was here
osdep.c: In function ‘ti_set_ip’:
osdep.c:202: warning: passing argument 2 of ‘ti->ti_set_ip’ from incompatible pointer type
osdep.c: In function ‘ti_alloc’:
osdep.c:211: warning: incompatible implicit declaration of built-in function ‘malloc’
osdep.c:213: error: ‘NULL’ undeclared (first use in this function)
osdep.c:214: warning: incompatible implicit declaration of built-in function ‘memset’
make[3]: *** [osdep.o] Error 1
make[3]: Leaving directory `/home/fabian/aircrack-ng-1.0-rc1/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/fabian/aircrack-ng-1.0-rc1/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/home/fabian/aircrack-ng-1.0-rc1/src'
make: *** [all] Error 2

I understand that its possible to install aircrack-ng under package manager but i cant seem to locate the file under the search tab although i have edited the settings in the repositories ( all of them ticked). Could anyone please kindly advise on the matter above or suggest a convenient way to install the application? Im totally a newbie in this area and i really need to get this working for my final year thesis entitled denial of service on IEEE 802.11 WLAN and the due date is rather soon :( And im sorry if my post is messy, as this is my first time posting a thread. Much help is appreciated. Thanks!

---

### Post by akekis on 2009-02-17
Anyone? I really need help here.

---

### Post by akekis on 2009-02-17
Guys, im really frustrated with this system as im totally clueless, any help please?? I need a guide to install aircrack-ng on 8.04.

---

### Post by akekis on 2009-02-18
Thanks everyone, this forum is rather helpful.

---

### Post by binbash on 2009-02-18
aircrack-ng is at repos why dont you just do apt-get install?

EDIT : BTW your error is caused because you dont have build-essential installed

sudo apt-get install build-essential

---

### Post by akekis on 2009-02-20
Thanks for the advice, Binbash, just got it installed via package manager :). However right now im facing some problems patching the driver as im using a IPW 3945. Could anyone advise on a step by step guide as how to patch and use the driver to inject packets? My deadline is near :(

---

### Post by wubbi on 2009-05-27
[CENTER][U][B]Hello everyone I need help 
[/B][/U][/CENTER]
 

I have an EEE 900 that I have ubunto 
  besides 
  I have aircrack-ng in 
  but I do not know how I get 
  in monitor mode it comes with an error 
 when I try sudo airmon-ng start wlna0

the error I get is here

wlan0            ath5k_pci - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)

wubbi@wubbi:~$ sudo ifconfig mon0 down
mon0: ERROR while getting interface flags: No such device

---

