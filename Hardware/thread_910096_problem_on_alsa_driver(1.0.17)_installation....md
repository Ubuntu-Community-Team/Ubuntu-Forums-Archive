---
title: "problem on alsa driver(1.0.17) installation..."
date: 2008-09-04
forum: Hardware
---

### Post by stathis21 on 2008-09-04
hi guys...
i hove got an acer aspire 5920g and i want to get HDMI worknig...
the only problem i have is to get sound working...
so i want to install latest alsa drivers...

in the end of command 'make' im allways take this error

```
CC [M]  /usr/src/alsa/alsa-driver-1.0.17/soc/soc-dapm.o
In file included from /usr/src/alsa/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/usr/src/alsa/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: &#931;&#964;&#951; &#963;&#965;&#957;&#940;&#961;&#964;&#951;&#963;&#951; ‘dapm_pop_time_store’:/*&#963;&#965;&#957;&#940;&#961;&#964;&#951;&#963;&#951; means function*/
/usr/src/alsa/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: &#963;&#966;&#940;&#955;&#956;&#945;: implicit declaration of function ‘strict_strtoul’ /*&#963;&#966;&#940;&#955;&#956;&#945; means error*/
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [compile] Error 2
```


any ideas how can i get this fixed???

sorry for my poor english...(im fron greecE:))..

---

### Post by jayashkoshal on 2008-11-25
even i am getting a similar kind of error..some of the text from the terminal is like:

/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/sound.c: In function ‘snd_request_other’:
/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/sound.c:100: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/alsa/alsa-driver-1.0.17-5.07/acore/init.o
/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/init.c: In function ‘snd_card_register’:
/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/init.c:568: warning: passing argument 5 of ‘device_create’ makes pointer from integer without a cast
/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/init.c:568: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/alsa/alsa-driver-1.0.17-5.07/acore/memory.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.17-5.07/acore/info.o
/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/info.c: In function ‘resize_info_buffer’:
/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/info.c:90: error: implicit declaration of function ‘PAGE_ALIGN’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.17-5.07/acore/info.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.17-5.07/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.17-5.07] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2


i guess there is some bug with 2.6.27.-7-generic kernel..
can somebody plz help

thanks in advance. :)

---

