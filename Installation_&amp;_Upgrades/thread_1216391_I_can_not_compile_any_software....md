---
title: "I can not compile any software..."
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by punia1979 on 2009-07-18
Hi, I have 2 distributions of ubuntu. On one laptop I have 9.04 and is working fine. But on the other laptop I have 8.1 and I can't compile madwifi drivers :( constantly getting this post:

  CC [M]  /home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
/home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/robert/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/robert/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/robert/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make: *** [modules] Error 2
root@5920g:/home/robert/Desktop/madwifi-0.9.4# 

trying this long time now... I have updated SVN and kernels doing everything on root account:

make clean
make
make install

does'nt work :( any solution?

---

### Post by Rocket2DMn on 2009-07-18
Have you done a
```
./configure
```
before your make and make install commands?  This isn't always necessary, but often times it is.  Also, do you know if the madwifi drivers are compatible with the kernel being used in 8.10 (2.6.27-14)?

---

