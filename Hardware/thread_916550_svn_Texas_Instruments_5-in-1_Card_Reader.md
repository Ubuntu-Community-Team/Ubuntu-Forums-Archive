---
title: "svn Texas Instruments 5-in-1 Card Reader"
date: 2008-09-11
forum: Hardware
---

### Post by macvr on 2008-09-11
hi , i' a noob and trying to get my Texas Instruments 5-in-1 Card Reader to work...

so i tried the method given in this post
[http://ubuntuforums.org/showpost.php?p=3726886&postcount=20]("http://ubuntuforums.org/showpost.php?p=3726886&postcount=20")

i have posted below the procedure i followed :

[PHP]$ svn co http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/
[/PHP]
```

A    driver/tifm_ms.c
A    driver/flash_bd.c
A    driver/jmb38x_xd.c
A    driver/tifm_core.c
A    driver/ul.sh
A    driver/mspro_block.c
A    driver/jmb38x_ms.c
A    driver/memstick.c
A    driver/linux
A    driver/linux/pci_ids.h
A    driver/linux/memstick.h
A    driver/linux/tifm.h
A    driver/linux/flash_bd.h
A    driver/linux/xd_card.h
A    driver/xd_card_ecc.c
A    driver/flash_bd-pp.c
A    driver/l.sh
A    driver/tifm_sd.c
A    driver/tifm_7xx1.c
A    driver/ms_block.c
A    driver/xd_card_blk.c
A    driver/Makefile
Checked out revision 239.

```
[PHP]~$ cd driver
[/PHP]
[PHP]~/driver$ make
[/PHP]
```
echo /home/oo/driver
/home/oo/driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/oo/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/oo/driver/built-in.o
  CC [M]  /home/oo/driver/tifm_core.o
  CC [M]  /home/oo/driver/tifm_7xx1.o
  CC [M]  /home/oo/driver/tifm_sd.o
  CC [M]  /home/oo/driver/memstick.o
/home/oo/driver/memstick.c: In function ‘h_memstick_read_dev_id’:
[COLOR="Red"]/home/oo/driver/memstick.c:347: error: implicit declaration of function ‘dev_emerg’
make[2]: *** [/home/oo/driver/memstick.o] Error 1
make[1]: *** [_module_/home/oo/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
[/COLOR]
```
[PHP]~/driver$ sudo make install[/PHP]
```
mkdir -p /lib/modules/2.6.24-19-generic
rm -f /lib/modules/2.6.24-19-generic/kernel/drivers/misc/tifm_core.ko
rm -f /lib/modules/2.6.24-19-generic/kernel/drivers/misc/tifm_7xx1.ko
rm -f /lib/modules/2.6.24-19-generic/kernel/drivers/mmc/tifm_sd.ko
install -c -m 644 tifm_core.ko tifm_7xx1.ko /lib/modules/2.6.24-19-generic/kernel/drivers/misc/
install: cannot stat `tifm_core.ko': No such file or directory
install: cannot stat `tifm_7xx1.ko': No such file or directory
make: *** [install] Error 1
```

how do i correct these errors?
how can i make the card reader work?

---

### Post by vkov_tinsky on 2008-09-12
> ```
[COLOR="Red"]/home/oo/driver/memstick.c:347: error: implicit declaration of function &#8216;dev_emerg&#8217;[/COLOR]
```

The reason this does not compile is because the *dev_emerg* macro (which lives include/linux/device.h in the kernel source tree) was only introduced very recently in kernel v2.6.25 (see [**here**]("https://www.linuxhq.com/kernel/v2.6/24-git17/include/linux/device.h") - the '+' next to the definition of dev_emerg indicates it's being added).

Since Ubuntu 8.04 has 2.6.24-21 as its latest kernel your best bet is to wait for Ubuntu 8.10 to be released which of course is next month (that should have kernel v.2.6.25 or later). Your other option is to manually get a newer kernel version but I can't help you with that since I don't have much experience with compiling custom kernels with Ubuntu.

Regards,
VT

---

### Post by macvr on 2008-09-12
> **vkov_tinsky said:**
> The reason this does not compile is because the *dev_emerg* macro (which lives include/linux/device.h in the kernel source tree) was only introduced very recently in kernel v2.6.25 (see [**here**]("https://www.linuxhq.com/kernel/v2.6/24-git17/include/linux/device.h") - the '+' next to the definition of dev_emerg indicates it's being added).

Since Ubuntu 8.04 has 2.6.24-21 as its latest kernel your best bet is to wait for Ubuntu 8.10 to be released which of course is next month (that should have kernel v.2.6.25 or later). Your other option is to manually get a newer kernel version but I can't help you with that since I don't have much experience with compiling custom kernels with Ubuntu.

Regards,
VT
the main page[http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver]("http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver")
>  Progress
Version 0.6 of the driver is included with stock 2.6.19 release of the linux kernel. Version 0.8 is available in two subversions for 2.6.20 and 2.6.21 kernels and should be used as a replacement for the shipped (and quite unfortunately, buggy) one. It is merged into main kernel, as of version 2.6.22.


how can i install version 0.6 or 0.8...

after download[to my desktop] of the file how do i proceed with those files?

---

### Post by vkov_tinsky on 2008-09-12
> Version 0.8 is available in two subversions for 2.6.20 and 2.6.21 kernels and should be used as a replacement for the shipped (and quite unfortunately, buggy) one. **It is merged into main kernel, as of version 2.6.22**
Since you have kernel v2.6.24-19 (judging by your first post) you already have v0.8 of that driver.

Also ...
> Early stages of development: 
tifm_xd - driver for xD/SmartMedia cards
 Assuming that information is up to date this means that it might not work even with the newest version yet. You could try to politely ask the author about whether xD should work yet or not.

Have you actually looked at what your logs say about whether the driver is loaded (and whether it mentions anything about xD)? Something along the lines of:
```
dmesg | grep tifm
```

Regards,
VT

---

### Post by macvr on 2008-09-12
> **vkov_tinsky said:**
> Since you have kernel v2.6.24-19 (judging by your first post) you already have v0.8 of that driver.

Also ...
 Assuming that information is up to date this means that it might not work even with the newest version yet. You could try to politely ask the author about whether xD should work yet or not.
well i know that linux doesnt support xD cards yet so i was wondering if i could make the Guest Windows XP OS recognize the card _reader_ the it would grab the device and i could use it to read xD cards
> **vkov_tinsky said:**
> Have you actually looked at what your logs say about whether the driver is loaded (and whether it mentions anything about xD)? Something along the lines of:
```
dmesg | grep tifm
```

the command does nothing!!!
no output!

---

### Post by macvr on 2008-09-12
ok...since the grep tifm didnt show any drivers

downloaded the 0.8 version file and extracted to a .driver folder
 i did the following```
cd .driver
``` ```
make
```and got the following error!
```
echo /home/oo/.driver
/home/oo/.driver
make -C /lib/modules/2.6.24-19-generic/build M=/home/oo/.driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/oo/.driver/tifm_7xx1.o
/home/oo/.driver/tifm_7xx1.c: In function ‘tifm_7xx1_probe’:
/home/oo/.driver/tifm_7xx1.c:344: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/oo/.driver/tifm_7xx1.c:344: error: (Each undeclared identifier is reported only once
/home/oo/.driver/tifm_7xx1.c:344: error: for each function it appears in.)
make[2]: *** [/home/oo/.driver/tifm_7xx1.o] Error 1
make[1]: *** [_module_/home/oo/.driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

```

but now ```
 ~$ dmesg | grep tifm
[18617.825108] tifm_sd: Unknown symbol tifm_eject
[18617.825206] tifm_sd: Unknown symbol tifm_register_driver
[18617.825519] tifm_sd: Unknown symbol tifm_unmap_sg
[18617.825616] tifm_sd: Unknown symbol tifm_map_sg
[18617.825721] tifm_sd: Unknown symbol tifm_unregister_driver
```

i dont know whats wrong!

---

### Post by vkov_tinsky on 2008-09-12
See my reply in another thread [_here_](http://ubuntuforums.org/showpost.php?p=5778068&postcount=70).

Also have a look at this: [http://gentoo-wiki.com/Acer_Ferrari_4005WLMi#FlashMedia](http://gentoo-wiki.com/Acer_Ferrari_4005WLMi#FlashMedia)

> Sony legacy MemoryStick support and xD cards are not supported at present, but some work is being done, so we may see them both supported, sooner or later
(And that person is talking about a version for kernel v2.6.25 so I don't think the curerntly available one will help.)

Regards,
VT

---

### Post by macvr on 2008-09-13
[COLOR="Red"]how safe is 2.6.24-21? i'm a noob so dont feel safe to try experimental headers:([/COLOR]

---

### Post by vkov_tinsky on 2008-09-13
Please stick to the [_other thread_](http://ubuntuforums.org/showthread.php?t=420721) for now until this is solved (or I've run out of ideas :D)

---

### Post by inspirra on 2009-07-17
```

user@host:/var/tmp/SRC$uname -rmsv
Linux 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64

user@host:/var/tmp/SRC$ svn export svn://svn.berlios.de/tifmxx/trunk/driver tifmxx
A    tifmxx
<...>
A    tifmxx/Makefile
Exported revision 291.

``````
user@host:/var/tmp/SRC/tifmxx$ LANG=C make
echo /var/tmp/SRC/tifmxx
/var/tmp/SRC/tifmxx
make -C /lib/modules/2.6.28-13-generic/build M=/var/tmp/SRC/tifmxx
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /var/tmp/SRC/tifmxx/xd_card_blk.o
/var/tmp/SRC/tifmxx/xd_card_blk.c:255: warning: initialization from incompatible pointer type
/var/tmp/SRC/tifmxx/xd_card_blk.c:256: warning: initialization from incompatible pointer type
/var/tmp/SRC/tifmxx/xd_card_blk.c: In function 'xd_card_submit_req':
/var/tmp/SRC/tifmxx/xd_card_blk.c:2175: error: implicit declaration of function 'end_queued_request'
/var/tmp/SRC/tifmxx/xd_card_blk.c: In function 'xd_card_resume_host':
/var/tmp/SRC/tifmxx/xd_card_blk.c:2873: warning: comparison of distinct pointer types lacks a cast
/var/tmp/SRC/tifmxx/xd_card_blk.c:2875: warning: comparison of distinct pointer types lacks a cast
make[2]: *** [/var/tmp/SRC/tifmxx/xd_card_blk.o] Error 1
make[1]: *** [_module_/var/tmp/SRC/tifmxx] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [all] Error 2

```Do anyone knows a patch for this problem?

---

