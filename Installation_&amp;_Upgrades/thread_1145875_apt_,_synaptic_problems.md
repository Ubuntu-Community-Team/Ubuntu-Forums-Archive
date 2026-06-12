---
title: "apt , synaptic problems"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by gadgeX on 2009-05-02
after upgrading to jaunty .. update manager no loger works , apt seg faults and synaptic does too .. 
syslog tells me > 

May  1 15:11:21 gnk-ubuntu kernel: [ 4572.493287] synaptic[6557]: segfault at d691dd70 ip b800e18d sp bf964a30 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[b7f6e000+bf000]
May  1 15:11:28 gnk-ubuntu kernel: [ 4579.275630] update-apt-xapi[6565]: segfault at d80f5d70 ip b7ba118d sp bfa04df0 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[b7b01000+bf000]


any ideas how to get my system back in working order ? 

thanks gadgeX

---

### Post by jtayl22 on 2009-05-06
This fixed it for me:

sudo rm /var/cache/apt/*bin

YMMV

---

### Post by becked on 2009-05-19
Thanks - that worked!

---

