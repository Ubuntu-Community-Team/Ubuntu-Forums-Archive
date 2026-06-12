---
title: "XFiDrv_Linux_Public_US_1.00 make problem"
date: 2009-12-10
forum: Hardware
---

### Post by synae on 2009-12-10
```
synae@Athena:~/Desktop/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.31-14-generic/build M=/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
synae@Athena:~/Desktop/XFiDrv_Linux_Public_US_1.00$ make install
Copy module files...
rm: cannot remove directory `/lib/modules/2.6.31-14-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1
synae@Athena:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 
```That's the problem I have when attempting to make so that I can install my sound card.  Any ideas?  Thanks for the help, I've read around and tried Googling but to no success.

Also if I try using sudo I get this.

```
synae@Athena:~$ cd $HOME/Desktop/XFiDrv_Linux_Public_US_1.00
synae@Athena:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.31-14-generic/build M=/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/synae/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
synae@Athena:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1
synae@Athena:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 

```

Thank you for any help.

---

