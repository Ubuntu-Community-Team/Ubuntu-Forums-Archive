---
title: "Kernel 2.6.31 (with Ubuntu patches 11.36) compilation errors"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by mo0nykit on 2009-09-28
Hello!

I'm learning how to compile and upgrade a Linux kernel. Here's what I did:
Starting from my home folder, ```
apt-get source linux-source-2.6.31 --download-only
mkdir linux
mv linux_2.6.31* linux
cd linux
```Then starting from *~/linux*, I have this pre-compilation script ```
# Pre-compilation script for source tree preparation and patching
tar xzvf linux_2.6.31.orig.tar.gz          # unpack the source code archive
cd linux-2.6.31                            # cd into the top of the source tree
patch -p1 -i ../linux_2.6.31-11.36.diff    # patch the source tree with Ubuntu patches

# (just following instructions from the Ubuntu Kernel/Compile page)
cd ~/linux/linux-2.6.31/debian
chmod a+x rules
cd ~/linux/linux-2.6.31/debian.master/scripts/misc
chmod a+x *
cd ~/linux/linux-2.6.31
debian/rules updateconfigs

cp ../.config ./.config                    # I already have a .config file backed up (since I was screwing up all the time)
cd /usr/src
sudo ln -s ~/linux/linux-2.6.31 linux      # add a symbolic link pointing to the source tree
```Now I run this command from the top of the source tree, saving the output to a file as well as printing it out to the standard output using **tee** ```
fakeroot make-kpkg --initrd --append-to-version=-kit kernel-image kernel-headers | tee -a ../compile-logs
```After a couple of hours or so, I don't get an installable **.deb** file. I also just found out the **tee** didn't write the error messages to **compile-logs**. Here are the errors I get (copied from the terminal):```
  CC [M]  ubuntu/lenovo-sl-laptop/lenovo-sl-laptop.o
  CC [M]  ubuntu/lirc/lirc_atiusb/lirc_atiusb.o
  CC [M]  ubuntu/lirc/lirc_bt829/lirc_bt829.o
  CC [M]  ubuntu/lirc/lirc_dev/lirc_dev.o
  CC [M]  ubuntu/lirc/lirc_gpio/lirc_gpio.o
In file included from ubuntu/lirc/lirc_gpio/lirc_gpio.c:56:
include/../drivers/media/video/bt8xx/bttvp.h:49:23: error: btcx-risc.h: No such file or directory
In file included from ubuntu/lirc/lirc_gpio/lirc_gpio.c:56:
include/../drivers/media/video/bt8xx/bttvp.h:141: error: field ‘top’ has incomplete type
include/../drivers/media/video/bt8xx/bttvp.h:142: error: field ‘bottom’ has incomplete type
include/../drivers/media/video/bt8xx/bttvp.h:420: error: field ‘main’ has incomplete type
ubuntu/lirc/lirc_gpio/lirc_gpio.c:82:1: warning: "dprintk" redefined
include/../drivers/media/video/bt8xx/bttvp.h:285:1: warning: this is the location of the previous definition
ubuntu/lirc/lirc_gpio/lirc_gpio.c: In function ‘get_queue’:
ubuntu/lirc/lirc_gpio/lirc_gpio.c:404: error: implicit declaration of function ‘bttv_get_gpio_queue’
ubuntu/lirc/lirc_gpio/lirc_gpio.c:404: warning: return makes pointer from integer without a cast
ubuntu/lirc/lirc_gpio/lirc_gpio.c: In function ‘init_module’:
ubuntu/lirc/lirc_gpio/lirc_gpio.c:515: error: implicit declaration of function ‘bttv_get_cardinfo’
make[4]: *** [ubuntu/lirc/lirc_gpio/lirc_gpio.o] Error 1
make[3]: *** [ubuntu/lirc/lirc_gpio] Error 2
make[2]: *** [ubuntu/lirc] Error 2
make[1]: *** [ubuntu] Error 2
make[1]: Leaving directory `/home/kit/linux/linux-2.6.31'
make: *** [debian/stamp/build/kernel] Error 2
$
```Am I missing something? Maybe I should disable the offending drivers in **make menuconfig** or something.

Thanks in advance for your help!

---

### Post by Partyboi2 on 2009-09-28
Hi, try installing the linux header package if you have not already
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by mo0nykit on 2009-09-28
**@Partyboi2**
Yes I've done that already. I did some experiments on my own and did the following

[LIST=1]
[*]Knowing that the problem lies with LIRC (Linux Infrared Remote Control), I disabled it in **make menuconfig** (Ubuntu Supplied Third-Party Device Drivers --> LIRC Device Support)
[*]Then I finished the compilation with ```
fakeroot ccache make-kpkg --initrd kernel-image kernel-headers
```
[/LIST]
I'll refer back to this part of the error message```
In file included from ubuntu/lirc/lirc_gpio/lirc_gpio.c:56:
include/../drivers/media/video/bt8xx/bttvp.h:49:23: error: btcx-risc.h: No such file or directory
```Looking around the directory```
~/linux/linux-2.6.31/drivers/media/video/bt8xx/
``` **btcx-risc.h** indeed doesn't exist.

However, **btcx-risc.h** resides a directory level higher, in```
~/linux/linux-2.6.31/drivers/media/video/
```Which brings me to my next question. Will copying **btcx-risc.h** to the *bt8xx* directory eliminate the compile problems presented by **LIRC**?

---

