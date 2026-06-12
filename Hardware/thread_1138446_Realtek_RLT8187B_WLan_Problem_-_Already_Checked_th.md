---
title: "Realtek RLT8187B WLan Problem - Already Checked the WifiDoc"
date: 2009-04-26
forum: Hardware
---

### Post by Stoupeace on 2009-04-26
I got this quote from another thread regarding this problem. The thread is marked solved, yet i cant seem to find a solution for my case

> **pjasnos said:**
> Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps

When i type ./makedrv it lists a bunch of stuff ending with "2 errors".

```
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.23.1-42.fc8/build M=/root/rtl8187b-modified/ieee80211 CC=gcc modules
make: *** /lib/modules/2.6.23.1-42.fc8/build: No such file or directory. Stop.
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.23.1-42.fc8/build M=/root/rtl8187b-modified/rtl8187 CC=gcc modules
make: *** /lib/modules/2.6.23.1-42.fc8/build: No such file or directory. Stop.
make: *** [modules] Error 2
```

When i type sudo ./wlan0up it lists some files that cant be read "No such file or directory", apparently because the last command didnt work right.

What can i do?

I am using Ubuntu 9.04

---

### Post by Stoupeace on 2009-04-26
Bump

---

