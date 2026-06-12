---
title: "Cant get wired or wireless on eee pc 1008HA"
date: 2009-08-30
forum: Hardware
---

### Post by IronFox on 2009-08-30
I've been following the how to and I got it working once, then I decided to try other linux flavors to see which one was right for my netbook.  After trying almost everything under the sun, I decided that ubuntu was the best.  But going back, I can't get the wired ethernet working.  I keep getting this:

```
root@jordan-netbook:/home/jordan# tar -xzvf [459]AR813X-linux-v1.0.0.9.tar.gz atl1e.7
at_osdep.h
copying
ldistrib.txt
readme
release_note.txt
src/
src/atl1c.h
src/atl1c_ethtool.c
src/atl1c_hw.c
src/atl1c_hw.h
src/atl1c_main.c
src/atl1c_param.c
src/atl1e.h
src/atl1e_ethtool.c
src/atl1e_hw.c
src/atl1e_hw.h
src/atl1e_main.c
src/atl1e_param.c
src/at_common.h
src/at_common_main.c
src/at_osdep.h
src/kcompat.c
src/kcompat.h

gzip: stdin: decompression OK, trailing garbage ignored
src/kcompat_ethtool.c
src/Makefile
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@jordan-netbook:/home/jordan# cd src
root@jordan-netbook:/home/jordan/src# make
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/jordan/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/jordan/src/at_common_main.o
  CC [M]  /home/jordan/src/atl1e_main.o
  CC [M]  /home/jordan/src/atl1c_main.o
  CC [M]  /home/jordan/src/atl1c_hw.o
  CC [M]  /home/jordan/src/atl1e_hw.o
  CC [M]  /home/jordan/src/atl1e_param.o
  CC [M]  /home/jordan/src/atl1c_param.o
  CC [M]  /home/jordan/src/atl1e_ethtool.o
  CC [M]  /home/jordan/src/atl1c_ethtool.o
  CC [M]  /home/jordan/src/kcompat.o
  LD [M]  /home/jordan/src/atl1e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jordan/src/atl1e.mod.o
  LD [M]  /home/jordan/src/atl1e.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
root@jordan-netbook:/home/jordan/src# make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/jordan/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
gzip -c ../atl1e.7 > atl1e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.28-11-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-11-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a || true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
man: 
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.

```
After make install, I do the insmod atl1e.ko and the ethernet wont work.  I've tried jaunty and intrepid but both are a no go.

---

### Post by finito on 2009-08-30
try adding sudo

---

