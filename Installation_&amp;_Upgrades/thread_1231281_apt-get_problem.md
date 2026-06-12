---
title: "apt-get problem"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by zelalem on 2009-08-04
Hi guys I was trying to install the package libcommoncpp2-1.6-0 (which is required by twinkle) using apt-get but it messed up every thing and then after I couldn't get apt-get working. I get the following error: 
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
......
apt-get: relocation error: apt-get: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

I can't update or install anything now. My ubuntu version is Hardy (8.04..2).

Please help me.

Thank you.

---

### Post by zelalem on 2009-08-05
Don't worry guys. I removed the entry that presumably libcommoncpp2-1.6-0 entered and included anotehr entry that points to the actual gcc directory in the /etc/ld.so.conf.d/libc.conf file and the problem is solved now.

Thank you

---

