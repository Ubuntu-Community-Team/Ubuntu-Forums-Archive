---
title: "b43 packet injection 2.6.28.xx kernel"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by afallenhope on 2009-09-12
Alright, I've been looking everywhere on how to install this dang thing.
so, I figured I'd post a how-to I guess you could call it.

[_Needed files_]
```

mac80211 patch - [mac80211_2.6.28-rc4-wl_frag+ack_v3.patch]("http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch")

```

First it's nice to keep your packages updated so let's update / upgrade any packages.

```
sudo apt-get update && sudo apt-get upgrade
```

Yehah! Up-to-date!
Now, install the source as well as the compiling utils.
```
cd /usr/src
sudo apt-get install linux-source-2.6.28 build-essential gawk bison linux-kernel-headers linux-headers-$(uname -r)

```

Right! If you see what's in the directory you should see linux-source-2.6.28.tar.gz2 if not.. sorry. I screwed up somewhere and I don't feel like backtracing. You get the general impression.

Moving on! Unzip it the source!
```
sudo tar -xjf linux-source-2.6.28.tar.gz2
cd linux-source-2.6.28/
```

Time to patch!
```
sudo wget http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch && sudo patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
```

Paaaaaaaatched. Let's make the module!
```
sudo cp /usr/src/linux-headers-$(uname -r)/.config ./
sudo make modules_prepare
sudo make -C /usr/src/linux-source-2.6.28/ M=/usr/src/linux-source-2.6.28/net/mac80211/ modules
sudo cp /usr/src/linux-source-2.6.28/net/mac80211/modules.order  ./

```

shouldn't have any more issues... now let's install the bugger!

```
sudo make modules_install
```

aaaand let's load it!
```
depmod -ae
modprobe b43
```

Now, you shouldn't have to reboot..
Test it out and see if it works.

```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor channel 6
sudo ifconfig wlan0 up
sudo aireplay -9 wlan0
```

Should see "injection is working"
if not, you broke it and owe me a twinky!

**NOTE:** in the beginning of everything if you don't want to type "sudo" for everything simply type "sudo -s" and that should make you root in the current dir you're in.

to go back into "managed mode" so that you can actually use the Internet.

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed channel 6 essid YOUR-AP-HERE key INSERT-SPECIAL-PASSWORD-HERE
sudo ifconfig wlan0 up
```

and you should be hunky-dori!
That's at least what I did and worked for me :)


**NOTE/UPDATE:** I noticed that I haven't added a bunch of "sudo"'s where they needed to be, thus causing the issue below. If you want to save yourself the trouble of writing "sudo"  before starting anything type 

```
sudo -i
``` 
than do the rest of the stuff minus the sudo.

---

### Post by scrubsJA on 2009-10-02
afallenhope

I followed your instructions to the letter and the following happened. I have no idea of what to do. Please help, Thanks

home@ubuntu:/usr/src$ cd linux-source-2.6.28
home@ubuntu:/usr/src/linux-source-2.6.28$ ls
arch           init                                      README
block          ipc                                       REPORTING-BUGS
COPYING        Kbuild                                    samples
CREDITS        kernel                                    scripts
crypto         lib                                       security
Documentation  mac80211_2.6.28-rc4-wl_frag+ack_v3.patch  sound
drivers        MAINTAINERS                               ubuntu
firmware       Makefile                                  usr
fs             mm                                        virt
include        net
home@ubuntu:/usr/src/linux-source-2.6.28$ sudo cp /usr/src/linux-headers-$(uname -r)/.config ./
home@ubuntu:/usr/src/linux-source-2.6.28$ make modules_prepare
scripts/kconfig/conf -s arch/x86/Kconfig

*** Error during update of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
home@ubuntu:/usr/src/linux-source-2.6.28$ make -C /usr/src/linux-source-2.6.28/ M=/usr/src/linux-source-2.6.28/net/mac80211/ modules
make: Entering directory `/usr/src/linux-source-2.6.28'
mkdir: cannot create directory `/usr/src/linux-source-2.6.28/net/mac80211//.tmp_versions': Permission denied

  WARNING: Symbol version dump /usr/src/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/linux-source-2.6.28/net/mac80211/main.o
Assembler messages:
Fatal error: can't create /usr/src/linux-source-2.6.28/net/mac80211/.tmp_main.o: Permission denied
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/textsearch.h:7,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:120,
                 from include/net/mac80211.h:17,
                 from /usr/src/linux-source-2.6.28/net/mac80211/main.c:11:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:256:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/textsearch.h:7,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:120,
                 from include/net/mac80211.h:17,
                 from /usr/src/linux-source-2.6.28/net/mac80211/main.c:11:
include/linux/mmzone.h:277: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from include/linux/scatterlist.h:6,
                 from /usr/src/linux-source-2.6.28/arch/x86/include/asm/dma-mapping.h:9,
                 from include/linux/dma-mapping.h:57,
                 from include/linux/dmaengine.h:29,
                 from include/linux/skbuff.h:29,
                 from include/linux/if_ether.h:120,
                 from include/net/mac80211.h:17,
                 from /usr/src/linux-source-2.6.28/net/mac80211/main.c:11:
include/linux/mm.h:437:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:485:62: warning: "NR_PAGEFLAGS" is not defined
make[1]: *** [/usr/src/linux-source-2.6.28/net/mac80211/main.o] Error 2
make: *** [_module_/usr/src/linux-source-2.6.28/net/mac80211] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.28'
home@ubuntu:/usr/src/linux-source-2.6.28$ cp /usr/src/linux-source-2.6.28/net/mac80211/modules.order  ./make -C /usr/src/linux-source-2.6.28/ M=/usr/src/linux-source-2.6.28/net/mac80211/ modules
cp: invalid option -- 'C'
Try `cp --help' for more information.
home@ubuntu:/usr/src/linux-source-2.6.28$ cp /usr/src/linux-source-2.6.28/net/mac80211/modules.order  ./
cp: cannot stat `/usr/src/linux-source-2.6.28/net/mac80211/modules.order': No such file or directory
home@ubuntu:/usr/src/linux-source-2.6.28$ make modules_install
scripts/kconfig/conf -s arch/x86/Kconfig

*** Error during update of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
mkdir: cannot create directory `/lib/modules//kernel': Permission denied
make: *** [_modinst_] Error 1
home@ubuntu:/usr/src/linux-source-2.6.28$ sudo make modules_install
scripts/kconfig/conf -s arch/x86/Kconfig
cp: cannot stat `/usr/src/linux-source-2.6.28/modules.order': No such file or directory
make: *** [_modinst_] Error 1
home@ubuntu:/usr/src/linux-source-2.6.28$ make modules_prepare/bin/sh: cannot create include/config/kernel.release: Permission denied
make: *** [include/config/kernel.release] Error 2
home@ubuntu:/usr/src/linux-source-2.6.28$ sudo cp /usr/src/linux-headers-$(uname -r)/.config ./
home@ubuntu:/usr/src/linux-source-2.6.28$ make modules_prepare
scripts/kconfig/conf -s arch/x86/Kconfig

*** Error during update of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
home@ubuntu:/usr/src/linux-source-2.6.28$  make -C /usr/src/linux-source-2.6.28/ M=/usr/src/linux-source-2.6.28/net/mac80211/ modules
make: Entering directory `/usr/src/linux-source-2.6.28'
mkdir: cannot create directory `/usr/src/linux-source-2.6.28/net/mac80211//.tmp_versions': Permission denied

  WARNING: Symbol version dump /usr/src/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/linux-source-2.6.28/net/mac80211/main.o
Assembler messages:
Fatal error: can't create /usr/src/linux-source-2.6.28/net/mac80211/.tmp_main.o: Permission denied
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/textsearch.h:7,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:120,
                 from include/net/mac80211.h:17,
                 from /usr/src/linux-source-2.6.28/net/mac80211/main.c:11:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:256:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/textsearch.h:7,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:120,
                 from include/net/mac80211.h:17,
                 from /usr/src/linux-source-2.6.28/net/mac80211/main.c:11:
include/linux/mmzone.h:277: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from include/linux/scatterlist.h:6,
                 from /usr/src/linux-source-2.6.28/arch/x86/include/asm/dma-mapping.h:9,
                 from include/linux/dma-mapping.h:57,
                 from include/linux/dmaengine.h:29,
                 from include/linux/skbuff.h:29,
                 from include/linux/if_ether.h:120,
                 from include/net/mac80211.h:17,
                 from /usr/src/linux-source-2.6.28/net/mac80211/main.c:11:
include/linux/mm.h:437:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:485:62: warning: "NR_PAGEFLAGS" is not defined
make[1]: *** [/usr/src/linux-source-2.6.28/net/mac80211/main.o] Error 2
make: *** [_module_/usr/src/linux-source-2.6.28/net/mac80211] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.28'
home@ubuntu:/usr/src/linux-source-2.6.28$ cp /usr/src/linux-source-2.6.28/net/mac80211/modules.order  ./
cp: cannot stat `/usr/src/linux-source-2.6.28/net/mac80211/modules.order': No such file or directory

---

### Post by afallenhope on 2009-10-27
As you can see in your error you're getting "permission denied" which generally means that you need to do things as "root" thus, you should use the special magic command. "sudo".

---

