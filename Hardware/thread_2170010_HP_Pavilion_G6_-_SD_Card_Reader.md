---
title: "HP Pavilion G6 - SD Card Reader"
date: 2013-08-24
forum: Hardware
---

### Post by mdonders on 2013-08-24
I installed Ubuntu 13.04 on a new HP Pavilion G6 I picked up from a friend and the only thing I cannot get working is the SD Card Reader. Here is what I have been able to figure out based on some research.

Based on some other websites I was able to determine that I have the RTS5209 from Realtek:
```
mattdonders@mattdondersubuntu:~/rts_pstor$ lspci | grep Realtek
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

```

I downloaded the driver from the Realtek website: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

I un-tarred the archive and tried to run make based on their README and get the following error.
```
mattdonders@mattdondersubuntu:~$ cd rts_pstor/
mattdonders@mattdondersubuntu:~/rts_pstor$ make
sed "s/RTSX_MK_TIME/`date +%y.%m.%d.%H.%M`/" timestamp.in > timestamp.h
cp -f ./define.release ./define.h
make -C /lib/modules/3.8.0-29-generic/build/ SUBDIRS=/home/mattdonders/rts_pstor modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
  CC [M]  /home/mattdonders/rts_pstor/rtsx.o
/home/mattdonders/rts_pstor/rtsx.c:916:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtsx_probe’
/home/mattdonders/rts_pstor/rtsx.c:1080:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtsx_remove’
/home/mattdonders/rts_pstor/rtsx.c:1106:11: error: ‘rtsx_probe’ undeclared here (not in a function)
/home/mattdonders/rts_pstor/rtsx.c:1107:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
/home/mattdonders/rts_pstor/rtsx.c:1107:24: error: ‘rtsx_remove’ undeclared here (not in a function)
/home/mattdonders/rts_pstor/rtsx.c:485:12: warning: ‘rtsx_control_thread’ defined but not used [-Wunused-function]
/home/mattdonders/rts_pstor/rtsx.c:596:12: warning: ‘rtsx_polling_thread’ defined but not used [-Wunused-function]
/home/mattdonders/rts_pstor/rtsx.c:745:13: warning: ‘quiesce_and_remove_host’ defined but not used [-Wunused-function]
/home/mattdonders/rts_pstor/rtsx.c:780:13: warning: ‘release_everything’ defined but not used [-Wunused-function]
/home/mattdonders/rts_pstor/rtsx.c:790:12: warning: ‘rtsx_scan_thread’ defined but not used [-Wunused-function]
/home/mattdonders/rts_pstor/rtsx.c:816:13: warning: ‘rtsx_init_options’ defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[2]: *** [/home/mattdonders/rts_pstor/rtsx.o] Error 1
make[1]: *** [_module_/home/mattdonders/rts_pstor] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
make: *** [default] Error 2
```

Is there anything else I can or should try to get this working? Thanks in advance!

---

### Post by jeffmings on 2014-01-04
Hello!

I had the same problem!  I found a solution at:
[http://dainaccio.wordpress.com/2013/07/14/realtek-sd-reader-mounting-problems-under-linux-mintubuntu/#more-836](http://dainaccio.wordpress.com/2013/07/14/realtek-sd-reader-mounting-problems-under-linux-mintubuntu/#more-836)

It requires you to remove the __devinit and __devexit keywords from the file rtsx.c that came with the download from RealTek.  After that, run the usual commands per README.TXT.

BTW, after you run depmod, you should be able to use modprobe  rts_pstor  and start using the card reader without re-booting.

Good Luck,
-Jeffm in Honolulu

---

