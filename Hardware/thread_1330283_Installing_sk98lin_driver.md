---
title: "Installing sk98lin driver"
date: 2009-11-18
forum: Hardware
---

### Post by ene_dene on 2009-11-18
I have Ubuntu 9.10, kernel 2.6.31-14-generic.
I bought a network card D-LINK DGE-530T. Ubuntu tries to use skge module to run the card, but it's not working properly. sk98lin module is needed. So I downloaded the driver from manufacturer, after running install script i get compiling error message:
```
+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.o
  CC [M]  /tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.o
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_init_device’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:399: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:439: error: ‘struct net_device’ has no member named ‘open’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:440: error: ‘struct net_device’ has no member named ‘stop’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:441: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:442: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:443: error: ‘struct net_device’ has no member named ‘set_mac_address’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:444: error: ‘struct net_device’ has no member named ‘do_ioctl’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:445: error: ‘struct net_device’ has no member named ‘change_mtu’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:448: error: ‘struct net_device’ has no member named ‘poll_controller’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:466: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:476: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:570: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:599: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:605: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:613: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:624: error: ‘struct net_device’ has no member named ‘open’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:625: error: ‘struct net_device’ has no member named ‘stop’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:626: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:627: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:628: error: ‘struct net_device’ has no member named ‘set_mac_address’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:629: error: ‘struct net_device’ has no member named ‘do_ioctl’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:630: error: ‘struct net_device’ has no member named ‘change_mtu’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:633: error: ‘struct net_device’ has no member named ‘poll_controller’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_resume’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1117: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_suspend’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1195: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘FreeResources’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1509: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1510: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘sk98lin_remove_device’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1690: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:1749: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeIsr’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2281: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2294: error: implicit declaration of function ‘netif_rx_schedule_prep’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2303: error: implicit declaration of function ‘__netif_rx_schedule’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeOpen’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2407: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeClose’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2727: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:2770: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeXmit’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:3006: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGePoll’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:3096: error: implicit declaration of function ‘__netif_rx_complete’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeNetPoll’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:3128: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeSetMacAddr’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4166: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeSetRxMode’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4223: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeChangeMtu’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4335: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeStats’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4456: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkGeIoctl’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:4761: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkDrvEvent’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6613: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c: In function ‘SkDrvEnterDiagMode’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6905: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6922: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.c:6923: error: ‘struct net_device’ has no member named ‘priv’
make[1]: *** [/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/skge.o] Error 1
make[1]: *** Waiting for unfinished jobs....
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c: In function ‘SkY2Isr’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:397: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c: In function ‘SkY2Xmit’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:503: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c: In function ‘AllocateAndInitLETables’:
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:2873: warning: cast to pointer from integer of different size
/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.c:2875: warning: cast from pointer to integer of different size
make[1]: *** [/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all/sky2.o] Error 1
make: *** [_module_/tmp/Sk98IEKQLJKoloqHRfCAbleQO/all] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
+++ Compiler error
```

Could someone explain to me what needs to be done to not get this error?

---

### Post by djwishbone on 2010-03-14
Did you ever get this to work?

---

### Post by ene_dene on 2010-03-15
> **djwishbone said:**
> Did you ever get this to work?
Negative.
I tried it o live CD openSUSE x64 and 32bit version. The card worked in 32bit version. I haven't tried it on 32 bit ubuntu since I don't use it, but it doesn't work on 64bit version for sure.

I solved the problem by not using the card anymore. :)

---

### Post by Odur on 2010-03-17
I've successfully compiled the sk98lin on Kubuntu 9.10 by doing this little modification to the installation script.

Open the file "functions" and replace all occurrences of "/source" with "/build".

After this the ./install.sh runs without problem and the driver module compiles smoothly.

Just remember to run it with bash
sudo bash ./install.sh

Good luck.

---

### Post by ene_dene on 2010-03-17
> **Odur said:**
> I've successfully compiled the sk98lin on Kubuntu 9.10 by doing this little modification to the installation script.

Open the file "functions" and replace all occurrences of "/source" with "/build".

After this the ./install.sh runs without problem and the driver module compiles smoothly.

Just remember to run it with bash
sudo bash ./install.sh

Good luck.

I haven't tried it for a while, I did what you wrote but again some kind of problem:
```
+++ Install mode: User
+++ Driver version: 10.81.5.3 (Oct-14-2009)
+++ Kernel version 2.6.31-20-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=x86_64
+++ Architecture: x86_64
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.6/
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/Makefile
2.6/skge.c
2.6/skproc.c
2.6/skdim.c
2.6/sky2.c
2.6/skethtool.c
common/
common/h/
common/h/lm80.h
common/h/mvyexhw.h
common/h/skaddr.h
common/h/skcsum.h
common/h/skdebug.h
common/h/skerror.h
common/h/skgedrv.h
common/h/skgehw.h
common/h/skgehwt.h
common/h/skgeinit.h
common/h/skgepnm2.h
common/h/skgepnmi.h
common/h/skgesirq.h
common/h/skgetwsi.h
common/h/skpcidevid.h
common/h/skqueue.h
common/h/skrlmt.h
common/h/sktimer.h
common/h/sktwsi.h
common/h/sktypes.h
common/h/skversion.h
common/h/skvpd.h
common/h/sky2le.h
common/h/xmac_ii.h
common/skaddr.c
common/skcsum.c
common/skgehwt.c
common/skgeinit.c
common/skgemib.c
common/skgepnmi.c
common/skgesirq.c
common/sklm80.c
common/skqueue.c
common/skrlmt.c
common/sktimer.c
common/sktwsi.c
common/skvpd.c
common/skxmac2.c
common/sky2le.c
common/vpdcheck.c
common/sk98lin.txt
common/sk98lin.htm
common/sk98lin.4
misc/
misc/Configure.help
misc/Kconfig

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
make -C /lib/modules/2.6.31-20-generic/build \
	KBUILD_SRC=/usr/src/linux-headers-2.6.31-20-generic \
	KBUILD_EXTMOD="/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all" -f /usr/src/linux-headers-2.6.31-20-generic/Makefile \
	
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/.tmp_versions ; rm -f /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/.tmp_versions/*
make -f /usr/src/linux-headers-2.6.31-20-generic/scripts/Makefile.build obj=/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all
   rm -f /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/built-in.o; ar rcs /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/built-in.o
  cc -Wp,-MD,/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/.skge.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.31-20-generic/include -I/usr/src/linux-headers-2.6.31-20-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.31-20-generic/ubuntu/include   -I/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm   -I/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skge)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/.tmp_skge.o /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c
  cc -Wp,-MD,/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/.sky2.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.31-20-generic/include -I/usr/src/linux-headers-2.6.31-20-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.31-20-generic/ubuntu/include   -I/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm   -I/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sky2)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/.tmp_sky2.o /tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/sky2.c
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c: In function ‘sk98lin_init_device’:
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c:624: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c: In function ‘SkGeTestMsi’:
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c:1963: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘int (*)(int,  void *)’
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c: In function ‘SkDrvEvent’:
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c:6680: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.c:7017: error: ‘struct net_device’ has no member named ‘priv’
make[2]: *** [/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all/skge.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/tmp/Sk98IFOlFZTGFmgNHgmWnLpmF/all] Error 2
make: *** [sub-make] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
+++ Compiler error
```

---

### Post by Odur on 2010-03-17
Have you download the most recent version of the driver? The one I got from Marvell was released in january this year.

I use the "Installation" option in the installer. Number one, that is.

---

### Post by ene_dene on 2010-03-17
> **Odur said:**
> Have you download the most recent version of the driver? The one I got from Marvell was released in january this year.

I use the "Installation" option in the installer. Number one, that is.
No, I haven't, that could be it. Could you give me a direct link, so that I don't make a mistake of downloading the wrong one?

---

### Post by Odur on 2010-03-17
I can't seem to find a direct link to the driver. But go to [www.marvell.com](www.marvell.com) click "Support" and choose a platform from the upper listbox to the right. You should choose "Linux 2.6 - Fedora" (Don't worry about the Fedora part).
Then download the 10.84.3.3 version of the driver.

---

### Post by ene_dene on 2010-03-17
> **Odur said:**
> I can't seem to find a direct link to the driver. But go to [www.marvell.com](www.marvell.com) click "Support" and choose a platform from the upper listbox to the right. You should choose "Linux 2.6 - Fedora" (Don't worry about the Fedora part).
Then download the 10.84.3.3 version of the driver.
Thank you very much, I've successfully installed the driver. But now I have a new problem.
I think that the old driver was "skge", and I need to load this "sk98lin".
I know about rmmod and modprobe, but I'd like to load only sk98lin driver on startup.
I've tried and put the line:
```
blacklist skge
``` in /etc/modprobe.d/blacklist.conf file and ```
sk98lin
``` line in /etc/modules, but after restart "skge" driver is loaded anyway and sk98lin driver is not loaded.

Do you know how to make this work automatically?

---

### Post by Odur on 2010-03-17
Do this, it'll make the blacklist work.
```
sudo update-initramfs -u
```

---

### Post by ene_dene on 2010-03-17
Thanks very much, I did it.

Are you satisfied with stability of this driver? I tried copying few larger files from my other machine and I had an error in transfer after a while:
```
rite failed: Broken pipe
lost connection
```

Are you experiencing the same problem?

---

### Post by Odur on 2010-03-17
Nope, it's steady as a rock here.

---

### Post by ene_dene on 2010-03-17
> **Odur said:**
> Nope, it's steady as a rock here.
Ok, glad to here that. Thanks again.

---

### Post by ultiva on 2010-04-07
Refreshing thread.
My question is - why there is no sk89lin driver in the Ubuntu 9.10 nor 10.04 ? This driver is needed by Marvell Yukon cards ex. the one present in my Sony Vaio - Marvell Yukon 88E8059 Gigabit Ethernet. Driver exists and works stable so I don't understand why force people to compile it on their own and do some kernel hacks for the successful compilation. Are there any plans to support this cards in Ubuntu ?

---

### Post by ene_dene on 2010-04-07
> **ultiva said:**
> Refreshing thread.
My question is - why there is no sk89lin driver in the Ubuntu 9.10 nor 10.04 ? This driver is needed by Marvell Yukon cards ex. the one present in my Sony Vaio - Marvell Yukon 88E8059 Gigabit Ethernet. Driver exists and works stable so I don't understand why force people to compile it on their own and do some kernel hacks for the successful compilation. Are there any plans to support this cards in Ubuntu ?
I'm not sure why is that. I also have Alfa AWUS036H wireless card that used to work on some kernels with patching and now it doesn't. That seems absurd but obliviously the kernel organization teams need better organization. It's a huge problem if you ask me.

---

### Post by neocheema on 2010-04-07
This post may be a bit off topic.  I'm using eBox (based on ubuntu 8.04) on my firewall machine and trying to install sk98lin for marvell's 8057 integrated card. 
And here is the problem. eBox doesn't have any means of compiling whatsoever, no gcc or g++ :( . And since ebox is anyway meant only for firewalling purposes, I'm not too keen on installing gcc etc on my machine. 
Is it possible that I can compile sk98lin on another ubuntu 8.04 machine and then copy and load the drivers on my ebox machine?

---

### Post by wipmonkey on 2010-05-10
> **Odur said:**
> I've successfully compiled the sk98lin on Kubuntu 9.10 by doing this little modification to the installation script.

Open the file "functions" and replace all occurrences of 

After this the ./install.sh runs without problem and the driver module compiles smoothly.

Just remember to run it with bash
sudo bash ./install.sh

Good luck.

worked for me :).. cli step by step:

goto [http://www.marvell.com/support.html](http://www.marvell.com/support.html) and get the latest linux 2.6 fedora driver and 
```

tar jxvvf install_vXXXX.tar.bz2
cd DriverInstall/
sed -i 's/\/source/\/build/g' functions
sed -i 's/\/bin\/sh/\/bin\/bash/g' install.sh
sudo ./install.sh

```

choose :
1) installation	
Y to "Do you want proceed?"
anykey
1) Do nothing

```

sudo rmmod sky2&&sleep 10&&sudo modprobe sk98lin
sudo echo "blacklist sky2" /etc/modprobe.d/blacklist-sky2.conf
sudo update-initramfs -u

```

---

### Post by flybytay on 2010-07-09
> **wipmonkey said:**
> 
```

sudo echo "blacklist sky2" /etc/modprobe.d/blacklist-sky2.conf

```
Thanks a lot. But this line of code does not function. I created and edited that file manually.

---

### Post by hirschma on 2010-08-01
> **flybytay said:**
> Thanks a lot. But this line of code does not function. I created and edited that file manually.

Aside from that error, the previous post to yours is missing a few steps that less experienced users may appreciate. Note that you have to have a compiler and the proper linux headers for your system installed. This all assumes that all admin has been done the "Debian Way", or the Ubuntu Way.

Get the driver from Marvell as per two posts up... then:

```

sudo apt-get install linux-headers-"`uname -r`" gcc
tar jxvvf install_vXXXX.tar.bz2
cd DriverInstall/
sed -i 's/\/source/\/build/g' functions
sed -i 's/\/bin\/sh/\/bin\/bash/g' install.sh
sudo ./install.sh

```

Then,

```
sudo echo "blacklist sky2" > /etc/modprobe.d/blacklist-sky2.conf
sudo update-initramfs -u
sudo reboot
```

Then check to see if it loaded:

```
dmesg | cat /var/log/dmesg | grep eth0

```

If you see "sky2", it didn't work :)

---

### Post by Odur on 2010-08-20
Marvell has released a new version about a month ago. With this release it's not necessary to edit "functions".

Just download, untar and do:
```
sudo bash ./install.sh
(choose install)
sudo echo "blacklist sky2" > /etc/modprobe.d/blacklist-sky2.conf
sudo update-initramfs -u
sudo reboot
```
The last three steps is not necessary if the driver is being update.

---

### Post by BinaryMn on 2010-12-20
See [https://bbs.archlinux.org/viewtopic.php?id=106785](https://bbs.archlinux.org/viewtopic.php?id=106785) and [http://www.alsvartr.de/?p=1104](http://www.alsvartr.de/?p=1104) for a patched version of this driver that will compile with 2.6.35.

---

### Post by mathia on 2011-03-30
Hi,

**[B]Installing Marvell Yukon driver on Ubuntu**:[/B] (tested with linux-2.6.37)

Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "e.g. 88E8057 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices    Linux 2.6 - v10.87.3.3

 $ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by tkoopa on 2011-08-27
I'm trying to fix this for my 88E8055 but when I try to download the fedora driver from [http://www.marvell.com/drivers/driverDisplay.do?driverId=153](http://www.marvell.com/drivers/driverDisplay.do?driverId=153) it returns the windows version. Does anyone have the install_v10.90.5.3.tar.bz2 file lying around ?

---

### Post by Odur on 2011-08-28
Here is a direct link to the file
[http://www.marvell.com/drivers/files/install_v10.90.5.3.tar.bz2]("http://www.marvell.com/drivers/files/install_v10.90.5.3.tar.bz2")

---

### Post by foresto on 2011-10-23
After googling around a bit, I see there are quite a few of us with Yukon ethernet troubles on Ubuntu.  In my case, starting a few releases ago, the 88E8056 Yukon-2 chip on my motherboard has been intermittently taking a long time (sometimes minutes) to establish a link at boot time.  Since it looks like the Ubuntu team have decided to stick with the old sky2 driver, I took it upon myself to package the latest sk98lin driver from Marvell.  It's currently available in my PPA:

[https://launchpad.net/~foresto/+archive/extradrivers](https://launchpad.net/~foresto/+archive/extradrivers)

**My package does the following:**

[LIST]
[*] Builds and installs the driver for the currently-running kernel.  (This includes updating the initrd image.)
[*] Adds the sk98lin source to DKMS, so it will be automatically rebuilt after kernel upgrades.
[*] Blacklists the sky2 module (which otherwise prevents the sk98lin module from loading).
[/LIST]

[SIZE="2"]**[COLOR="SeaGreen"]If you use it, please let me know how it works for you.[/COLOR]**[/SIZE]

**Note:**

I have only tested this on an i386 installation with a Marvell 88E8056 chip.  It should work with amd64 and lots of other Yukon-series chips, but I just won't know until I hear back from you folks.

This package is available for Ubuntu Natty and Oneiric.

You'll probably want to remove any non-stock ethernet drivers you've already installed, lest they conflict with this one.

I didn't blacklist the skge driver because I'm not sure what circumstances cause it to load, or whether it prevents sk98lin from loading.  Reports on this are welcome.

Remember to reboot after installing, to see if the new driver loads automatically.

---

### Post by Rufy on 2012-01-03
Thought I'd let you know since there are no replies for 2 months...  I just installed your ppa on Mint 12 and it worked perfectly!  I was dreading upgrading to kernel v3 because I *knew* sky2 was gonna break, and it did.  And Marvel still hasn't fixed the compile issues with the latest version of the driver install, so I was also dreading digging through all that to figure out what went wrong.  Now I don't have to!  Back to full duplex ethernet, yay...  you'd think that wouldn't be difficult by now...

Thanks!

Chris

---

### Post by Kevin8787 on 2012-01-06
Hi there,

Running an Acer Veriton M410 running Ubuntu 11.10 x86_64 using the 3.0.0-12-generic kernel and the NIC is the Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 20)

By default after the install of Oneric it was using the sky2 driver. Since I had no internet connectivity I went out and grabbed patch and dkms from packages.ubuntu.com via a laptop and was able to install both of them along with your debian package containing the sk98lin driver.

Upon reboot, even with sky2 added to the /etc/modprobe.d/blacklist.conf file lspci -v was still showing sky2 as the driver being used. I modprobe -r that bad boy and load up sk98lin but even then I cannot seem to get an IP address.

Some interesting tidbits from dmesg:

When using the sky2 driver I see frequent sky2 0000:02:00.0: PCI hardware error (0x2010). Google searches suggesting using the Marvell driver over the sky2. Tried using the one directly off the Marvell website as well as this debian package but neither have proven to do the trick just yet.

It should be noted that if I bump back down to the 32 bit version of Ubuntu (10.04 or 11.10) networking is fine. I've pretty much reached the extent of my kernel driver knowledge and at this point, short of buying an independent NIC I'm not sure what I can do to get this Marvell NIC working. 

Anyone else dealing with this?

---

### Post by Gannet on 2012-02-12
Hello to all. I have an Asus P5B Deluxe motherboard with two integrated Marvell network adapters on it: 88E8001 and 88E8056. The problem is that after some time I'm loosing connection through IPv6. And the only way to recover it I found running: ifconfig eth0 down, ifconfig eth0 up. After that connection works for some time but then it loses again. More of that, using ifconfig down and ifconfig up command works not each time even for connection through IPv4. Can anyone tell me is installing sk98lin driver from Marvell website fixes my problem or not? Thanks.

---

### Post by dbuttric on 2012-03-10
I have an Oneiric install on an ASUS P5LD2.

I have applied the Extra Drivers PPA from Forest. That helped alot.

But now when my machine boots, the ethernet interface does not get an address.

ifup eth0 reports that the interface is configured. But no address assigned.
if I ifdown eth0 and then ifup eth0, everything is fine.

Has anyone seen this before? What can I do to debug it? What can I do to fix it?

Thanks very much.

David

---

### Post by algorhythm on 2012-03-19
> **foresto said:**
> After googling around a bit, I see there are quite a few of us with Yukon ethernet troubles on Ubuntu.  In my case, starting a few releases ago, the 88E8056 Yukon-2 chip on my motherboard has been intermittently taking a long time (sometimes minutes) to establish a link at boot time.  Since it looks like the Ubuntu team have decided to stick with the old sky2 driver, I took it upon myself to package the latest sk98lin driver from Marvell.  It's currently available in my PPA:

[https://launchpad.net/~foresto/+archive/extradrivers](https://launchpad.net/~foresto/+archive/extradrivers)

[SIZE="2"]**[COLOR="SeaGreen"]If you use it, please let me know how it works for you.[/COLOR]**[/SIZE]

I gave the oneiric version a go (I am on debian wheezy).  I have a Marvell 88E8053 chip.

There was no change after an install and reboot, so I tried upgrading the kernel -- I suspect that won't work either because the sk98lin compile threw an error:

```
Preconfiguring packages ...
(Reading database ... 194068 files and directories currently installed.)
Preparing to replace at 3.1.12-1 (using .../archives/at_3.1.13-1_i386.deb) ...
Stopping deferred execution scheduler: atd.
Unpacking replacement at ...
Selecting previously deselected package linux-image-3.2.0-2-686-pae.
Unpacking linux-image-3.2.0-2-686-pae (from .../linux-image-3.2.0-2-686-pae_3.2.9-1_i386.deb) ...
Selecting previously deselected package linux-doc-3.2.
Unpacking linux-doc-3.2 (from .../linux-doc-3.2_3.2.9-1_all.deb) ...
Processing triggers for man-db ...
Setting up at (3.1.13-1) ...
Starting deferred execution scheduler: atd.
Setting up linux-image-3.2.0-2-686-pae (3.2.9-1) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-2-686-pae /boot/vmlinuz-3.2.0-2-686-pae
[B]Error! Bad return status for module build on kernel: 3.2.0-2-686-pae (i686)
Consult /var/lib/dkms/sk98lin/10.91.2.3/build/make.log for more information.[/B]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-2-686-pae /boot/vmlinuz-3.2.0-2-686-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-2-686-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-2-686-pae /boot/vmlinuz-3.2.0-2-686-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-2-686-pae /boot/vmlinuz-3.2.0-2-686-pae
Generating grub.cfg ...

```
And the contents of the make.log...

```
DKMS make.log for sk98lin-10.91.2.3 for kernel 3.2.0-2-686-pae (i686)
Tue Mar 20 13:46:52 EST 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-2-686-pae'
  LD      /var/lib/dkms/sk98lin/10.91.2.3/build/built-in.o
  CC [M]  /var/lib/dkms/sk98lin/10.91.2.3/build/skge.o
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:396:2: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:396:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:396:2: warning: (near initialization for ‘sky2_netdev_ops.ndo_validate_addr’) [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:410:2: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:410:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:410:2: warning: (near initialization for ‘skge_netdev_ops.ndo_validate_addr’) [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c: In function ‘XmitFrameSG’:
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:3809:8: error: incompatible type for argument 2 of ‘pci_map_page’
/usr/src/linux-headers-3.2.0-2-common/include/asm-generic/pci-dma-compat.h:43:1: note: expected ‘struct page *’ but argument is of type ‘struct <anonymous>’
make[3]: *** [/var/lib/dkms/sk98lin/10.91.2.3/build/skge.o] Error 1
make[2]: *** [_module_/var/lib/dkms/sk98lin/10.91.2.3/build] Error 2
make[1]: *** [sub-make] Error 2
make: *** [all] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-2-686-pae'

```
This is just me trying out following instructions -- I have more work to do in terms of trying other options, digging deeper in the kernel etc, but you asked to be let known how it works, so... feel free to give further instructions :)

---

### Post by adamant715 on 2012-04-05
Did you manage to make it work under Kernel 3.2? I'm currently running 12.04 and the connection randomly stops working since it's using the sky2 driver.

---

### Post by foresto on 2012-07-22
Hi, all.  I have updated my sk98lin-dkms package to the latest version from Marvell and packaged it for Ubuntu Precise.  Initial testing on my own system (kernel 3.2.0-26-generic-pae) looks good.

[https://launchpad.net/~foresto/+archive/extradrivers/](https://launchpad.net/~foresto/+archive/extradrivers/)

A few Ubuntu Oneiric users who tried my last package reported that although sk98lin built and installed correctly, the sky2 driver was still in use after they rebooted.  I'm not sure why, but it seems that DKMS either failed to add the "blacklist sky2" line in /etc/modprobe.d/ or failed to rebuild the kernel's initrd file afterward.  This could be a DKMS bug.  In any case, taking care of those things manually apparently fixed the problem.

Please keep the comments coming.

Enjoy!

---

### Post by antler on 2012-07-23
> **foresto said:**
> 

[SIZE="2"]**[COLOR="SeaGreen"]If you use it, please let me know how it works for you.[/COLOR]**[/SIZE]



Thank you so much! It works with my setup of a "Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)" on AMD64. I'm using Ubuntu 12.04 with the generic 3.2.0-26 kernel.

---

### Post by AntiKris on 2012-08-10
Just wanted to throw in my two cents.  I've tried installing your driver, and manually blacklisting sky2, but that damn driver keeps loading at boot.  I even ran Marvell's version, and elected to 'remove' sky2, but it's like a cockroach infestation.  Any ideas?

Also, as far as the update-initramfs stage goes (I'm noobish), I think the error in updating initrd is due to this error:

"dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces"  <---this appears 4 times, then it quits with

"update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic'

---

### Post by foresto on 2012-08-10
I've never seen that error message before, but out of curiosity, what is the output when you run uname -r on your system?

This might be related:
[http://ubuntuforums.org/showthread.php?t=1601208](http://ubuntuforums.org/showthread.php?t=1601208)

---

### Post by AntiKris on 2012-08-10
uname -r gives me 3.2.0-24-generic

---

### Post by venerable13 on 2012-09-24
Hi, doesn't works for me on Ubuntu 12.04 3.2.0-31-generic-pae, card 88E8072. I installed your last version, can I do anything after install it.

If I have to rebuild my kernel put please all the necessary instructions.

1.Install your repos
2.add line "blacklist sky2" to /etc/modprobe.d/blacklist.conf? I have to do this? Sure? How I can check that sky2 still working? 
3.Rebuild? How?

Thanks for your effort.

---

### Post by Gannet on 2012-09-24
I'm using built-in distro-driver for my network adapters. And now they works fine. The problem was in provider. Damn it.

---

### Post by venerable13 on 2012-09-25
Thanks for this comment. Do you want to say that doing nothing it works for you?

What have I to do? Because my ethernet leds stay off, xd.

---

### Post by Gannet on 2012-09-25
> **venerable13 said:**
> Thanks for this comment. Do you want to say that doing nothing it works for you?

What have I to do? Because my ethernet leds stay off, xd.

No, not nothing. I just kept going on kicking my Internet provider and he fix the problem with IPv6 at last. The thing was in network solicitation request working different in windows and in Linux.

I don't know what's the problem in your case. But my adapters works fine now. It's: Marvell 88E80001 and 88E8056 (P5B Deluxe motherboard).

---

### Post by LaBanane on 2012-10-03
Hello everyone !

I have the same issue here.

I managed to upgrade my Ubuntu server 10.04 to 12.04 and apply the solution of foresto.
(Thanks to you by the way ;) )

But I still lost my PCI-E Ethernet card ! Yeah this is very weird. Sometime my eth0 disappear :-k ... 

Running on my server I have a script which pings every 3 minutes a monitoring server. When the issue comes my server can't ping my monitoring anymore, but when I try to ssh I managed to connect to my server. Then I can't see my PCI-E Ethernet card (not in lspci, not in lshw).
When I'm reboot my server, the eth0 "wake up" again and work for some time.

I was thinking it's a driver issue but obviously it's more ? Sk89lin doesn't work better than sky2 at first look.

In attachement a part of my SYSLOG. According to my monitoring system my server stop pings at 14:09, but i can't see anything.

If someone has any idea ?


*sorry for the bad English this is not my main language.



Here some information:

# ifconfig
```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:43ff:fe01:184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353873 (353.8 KB)  TX bytes:23268 (23.2 KB)
          Interrupt:52 Memory:fe620000-0 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:10.98.1.2  Bcast:10.98.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de9c:52ff:fe07:cbf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:320766 (320.7 KB)  TX bytes:2456729 (2.4 MB)
          Interrupt:51 Memory:fe420000-0 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:336 (336.0 B)  TX bytes:336 (336.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.16.99.1  P-t-P:172.16.99.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING  MTU:1500  Metric:1
          RX packets:2212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:127499 (127.4 KB)  TX bytes:0 (0.0 B)

```

# lspci
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)

```

# lshw -c network
```

  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 20
       serial: XX:XX:XX:XX:XX:XX
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sk98lin driverversion=10.92.1.3 (01) duplex=full firmware=N/A ip=192.168.2.1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:52 memory:fe620000-fe623fff ioport:e000(size=256) memory:fe600000-fe61ffff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 11
       serial: XX:XX:XX:XX:XX:XX
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sk98lin driverversion=10.92.1.3 (01) duplex=full firmware=N/A ip=10.98.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:51 memory:fe420000-fe423fff ioport:d000(size=256) memory:fe400000-fe41ffff

```

# lsmod | grep sk
```

sk98lin               171780  2 

```

# modprobe -l | grep sk
```

kernel/crypto/algif_skcipher.ko
kernel/drivers/net/ethernet/marvell/skge.ko
kernel/drivers/net/ethernet/marvell/sky2.ko
kernel/drivers/net/fddi/skfp/skfp.ko
kernel/drivers/net/tokenring/skisa.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-gp8psk.ko
kernel/drivers/staging/comedi/drivers/skel.ko
kernel/drivers/mtd/nand/diskonchip.ko
kernel/net/sched/act_skbedit.ko
updates/dkms/sk98lin.ko

```

# cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp

```

# cat /etc/modprobe.d/blacklist.conf 
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

# lsb_release -a
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```

---

### Post by pansapiens on 2012-10-10
Hi Foresto, I really appreciate your work on this module - my machine (~2008 iMac) is barely usable without sk98lin due to a bug in sky2.

The latest version (10.92.1.3-0~ppa2) seems to be failing to compile against the 3.2.0-31-generic kernel on Ubuntu 12.04.

# cat /var/lib/dkms/sk98lin/10.91.2.3/build/make.log

```

DKMS make.log for sk98lin-10.91.2.3 for kernel 3.2.0-31-generic (x86_64)
Thu Oct 11 10:58:49 EST 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-31-generic'
  LD      /var/lib/dkms/sk98lin/10.91.2.3/build/built-in.o
  CC [M]  /var/lib/dkms/sk98lin/10.91.2.3/build/skge.o
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:396:2: error: unknown field ‘ndo_set_multicast_list’ specified in initialiser
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:396:2: warning: initialisation from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:396:2: warning: (near initialisation for ‘sky2_netdev_ops.ndo_validate_addr’) [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:410:2: error: unknown field ‘ndo_set_multicast_list’ specified in initialiser
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:410:2: warning: initialisation from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:410:2: warning: (near initialisation for ‘skge_netdev_ops.ndo_validate_addr’) [enabled by default]
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c: In function ‘XmitFrameSG’:
/var/lib/dkms/sk98lin/10.91.2.3/build/skge.c:3809:8: error: incompatible type for argument 2 of ‘pci_map_page’
include/asm-generic/pci-dma-compat.h:43:1: note: expected ‘struct page *’ but argument is of type ‘struct <anonymous>’
make[2]: *** [/var/lib/dkms/sk98lin/10.91.2.3/build/skge.o] Error 1
make[1]: *** [_module_/var/lib/dkms/sk98lin/10.91.2.3/build] Error 2
make: *** [sub-make] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-31-generic'

```

Since there isn't any way to report bugs to a PPA (yet), I thought I'd just leave this here ...

Thanks !

---

### Post by chiefwilson on 2012-10-30
> **foresto said:**
> Hi, all.  I have updated my sk98lin-dkms package to the latest version from Marvell and packaged it for Ubuntu Precise.  Initial testing on my own system (kernel 3.2.0-26-generic-pae) looks good.

[https://launchpad.net/~foresto/+archive/extradrivers/](https://launchpad.net/~foresto/+archive/extradrivers/)

A few Ubuntu Oneiric users who tried my last package reported that although sk98lin built and installed correctly, the sky2 driver was still in use after they rebooted.  I'm not sure why, but it seems that DKMS either failed to add the "blacklist sky2" line in /etc/modprobe.d/ or failed to rebuild the kernel's initrd file afterward.  This could be a DKMS bug.  In any case, taking care of those things manually apparently fixed the problem.

Please keep the comments coming.

Enjoy!

Foresto, thanks many! I installed your package tonight as I was having issues with the Sky2 driver. In fact, my issue was compounded because I was running a headless server, so I live by my network connection (OpenSSH). Every time the Sky2 driver failed me, I had to pull the disk and load it on my other machine, reinstall linux, and re-assemble my array. Here is an output:

**lshw -class network**
  *-network
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 16
       serial: 00:26:2d:00:56:50
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sk98lin [COLOR="Red"]driverversion=10.92.1.3 [/COLOR](01) duplex=full firmware=N/A ip=192.168.*.*** latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:f0300000-f0303fff ioport:2000(size=256) memory:80300000-8031ffff

---

### Post by djcla on 2013-01-14
help i am being thick but if i add the repo then type apt-get install sk98lin-dkms it says it cant find the package the other one listed on the site seems to work ok though , any ideas?

---

### Post by Xanko on 2013-02-23
I have the follow make.log for kernel version 3.5
> 

DKMS make.log for sk98lin-10.92.1.3 for kernel 3.5.0-21-generic (x86_64)
Sat Feb 23 13:03:41 EST 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  LD      /var/lib/dkms/sk98lin/10.92.1.3/build/built-in.o
  CC [M]  /var/lib/dkms/sk98lin/10.92.1.3/build/skge.o
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:315:2: error: unknown field &#8216;get_sg&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:315:14: error: &#8216;ethtool_op_get_sg&#8217; undeclared here (not in a function)
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:317:2: error: unknown field &#8216;get_tx_csum&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:317:18: error: &#8216;ethtool_op_get_tx_csum&#8217; undeclared here (not in a function)
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:324:2: error: unknown field &#8216;get_rx_csum&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:324:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:324:2: warning: (near initialization for &#8216;sk98lin_ethtool_ops.set_coalesce&#8217;) [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:339:2: error: unknown field &#8216;set_sg&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:339:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:339:2: warning: (near initialization for &#8216;sk98lin_ethtool_ops.get_ringparam&#8217;) [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:340:2: error: unknown field &#8216;set_tx_csum&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:340:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:340:2: warning: (near initialization for &#8216;sk98lin_ethtool_ops.set_ringparam&#8217;) [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:341:2: error: unknown field &#8216;set_rx_csum&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:341:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:341:2: warning: (near initialization for &#8216;sk98lin_ethtool_ops.get_pauseparam&#8217;) [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:349:2: error: unknown field &#8216;get_tso&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:349:14: error: &#8216;ethtool_op_get_tso&#8217; undeclared here (not in a function)
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:350:2: error: unknown field &#8216;set_tso&#8217; specified in initializer
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:350:2: warning: initialization from incompatible pointer type [enabled by default]
/var/lib/dkms/sk98lin/10.92.1.3/build/skge.c:350:2: warning: (near initialization for &#8216;sk98lin_ethtool_ops.begin&#8217;) [enabled by default]
make[2]: *** [/var/lib/dkms/sk98lin/10.92.1.3/build/skge.o] Error 1
make[1]: *** [_module_/var/lib/dkms/sk98lin/10.92.1.3/build] Error 2
make: *** [sub-make] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'



Does the fact that the package is listed as i386 and I am trying to install on X86_64 have anything to do with the problem?

---

### Post by GroundZero on 2013-02-24
Hi everyone I have problems with sky2 driver for a very long time now.I have tried installing driver from marvels page : [http://www.marvell.com/support/downloads/search.do](http://www.marvell.com/support/downloads/search.do) ,
specifically :install_v10.92.1.3.tar.bz2

but with little success.Can someone tell me how to install this driver on Linux 3.5 with Ubuntu 12.10.

I tried deb from ppa added on this page but with little to no success.I have 2 computers that use this driver,one is x64 other 86.

---

### Post by Xanko on 2013-04-06
Marvell did release a driver that is compatible with 3.x, I have not had time to try and get it setup however.

---

### Post by foresto on 2013-04-12
Hi, folks.

I am no longer maintaining the sk98lin-dkms package because I no longer have hardware that works with that driver. The last package I uploaded to my PPA was for Ubuntu 12.04 (Precise). It's possible that the .deb file for that release might work on Quantal and newer releases, but I have no way of testing it, and I certainly cannot support it.

I would welcome someone skilled in driver builds and deb packaging to take over from here using their own PPA. Launchpad says there were over a hundred people using my package on Precise, so I imagine there are still quite a few who would appreciate the effort as they move to Ubuntu Quantal and newer releases.

Marvell releases new Yukon driver sources here:
[http://www.marvell.com/support/downloads/](http://www.marvell.com/support/downloads/)

Thanks for the feedback while I was maintaining the package, and good luck!

---

