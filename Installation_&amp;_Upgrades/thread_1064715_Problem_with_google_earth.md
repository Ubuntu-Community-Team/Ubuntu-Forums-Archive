---
title: "Problem with google earth"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by shanto_eee on 2009-02-09
Hi
i have installed google earth after downloading the file from googleearth site. Its installs fine. but when i open the program it starts and then and then closes. what might be the problem. I am sending the terminal code commands:
-----------------------------------------------------------------------
root@shanto:~# cd /home/shanto/bakupinstallers/Gearth
root@shanto:/home/shanto/bakupinstallers/Gearth# chmod +x GoogleEarthLinux.bin
root@shanto:/home/shanto/bakupinstallers/Gearth# sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
[B]root@shanto:/home/shanto/bakupinstallers/Gearth# googleearth
Warning: Unable to create prefs directory '/root/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
root@shanto:/home/shanto/bakupinstallers/Gearth# [/B]
---------------------------------------------------------------
can u help me fixing this up??

---

