---
title: "Compiling, make - error 2"
date: 2008-09-25
forum: General Help
---

### Post by dioltas on 2008-09-25
Hi all.
Recently when compiling make is giving me Error 2 and I can't seem to compile anything. At the moment I am trying to compile drivers for a wireless usb adapter, an ALFA AWUS036H to be precise.

I have attached the readme that comes with the adapter. It says to run two scripts, makedrv and wlan0up. I attached both of these too. The makedrv one just extracts some stuff from an archive and then runs make. The wlan0up one just loads some modules and starts the adapter I think, but I'm no expert on this stuff.

Here is the output when I run the makedrv script:

```


# ./makedrv 
ieee80211/
ieee80211/license
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_rx.c
ieee80211/tags
ieee80211/ieee80211_crypt_tkip.c
ieee80211/Makefile
ieee80211/readme
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211.h
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt.h
rtl8187/
rtl8187/license
rtl8187/r8180_rtl8225z2.c
rtl8187/r8180_rtl8225.h
rtl8187/r8187_led.c
rtl8187/r8180_93cx6.h
rtl8187/r8180_wx.h
rtl8187/r8180_hw.h
rtl8187/copying
rtl8187/r8187_led.h
rtl8187/r8180_pm.h
rtl8187/tags
rtl8187/r8187.h
rtl8187/Makefile
rtl8187/r8180_rtl8225.c
rtl8187/readme
rtl8187/install
rtl8187/.tmp_versions/
rtl8187/.tmp_versions/r8187.mod
rtl8187/changes
rtl8187/r8180_wx.c
rtl8187/r8180_pm.c
rtl8187/r8187_core.c
rtl8187/r8180_93cx6.c
rtl8187/authors
rtl8187/ieee80211.h
rtl8187/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:421: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_stop_scan’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:495: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_abort’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:915: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_stop_protocol_rtl’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2120: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: (Each undeclared identifier is reported only once
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: for each function it appears in.)
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2230:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2231:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2232:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2233:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2234:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_free’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2255: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
make[2]: *** [/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o
In file included from /home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:64:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8180_proc_module_init’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: ‘proc_net’ undeclared (first use in this function)
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: (Each undeclared identifier is reported only once
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: for each function it appears in.)
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8180_proc_module_remove’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:456: error: ‘proc_net’ undeclared (first use in this function)
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:730: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:1648: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2054:77: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2055:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2056:80: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2057:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function ‘rtl8187_usb_probe’:
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2938: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2956: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
make[2]: *** [/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/jack/ALFA/1/rtl8187_linux_26.1025.0328.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

```

I'm running the script as root. I've been searching for a solution to this, but can't seem to find one.
Any help would be really appreciated.

---

### Post by dioltas on 2008-09-27
bump

Maybe this is because the sources I'm trying to comple are just not compatible with ubuntu. I tried to compile and install nmap, and I had no problems...

When I tried to compile aircrack-ng I got this output:

```
me@mylaptop:~/aircrack-ng-1.0-rc1$ make
make -C src all
make[1]: Entering directory `/home/jack/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/jack/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/jack/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o radiotap-parser.o radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[3]: Leaving directory `/home/jack/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/jack/aircrack-ng-1.0-rc1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
aircrack-ng.c: In function &#8216;do_wpa_crack&#8217;:
aircrack-ng.c:4026: warning: implicit declaration of function &#8216;HMAC&#8217;
aircrack-ng.c:4026: warning: implicit declaration of function &#8216;EVP_sha1&#8217;
aircrack-ng.c:4032: warning: implicit declaration of function &#8216;EVP_md5&#8217;
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/jack/aircrack-ng-1.0-rc1/src'
make: *** [all] Error 2

```

Surely someone has had this problem before.
Can any linux gurus out there tell me what I'm missing?

I'm thinking maybe I'm missing some files or libraries, but I don't know which.

---

