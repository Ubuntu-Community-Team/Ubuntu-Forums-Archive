---
title: "apt-get package dependency errors"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by veggiefish on 2009-09-11
Hi,

Please can someone help me fix this, since its making my system very slow for some reason!

```

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
user@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libqt4-qt3support sun-java6-bin
The following packages will be upgraded:
  libqt4-qt3support sun-java6-bin
2 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
3 not fully installed or removed.
Need to get 0B/30.1MB of archives.
After this operation, 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 237806 files and directories currently installed.)
Preparing to replace libqt4-qt3support 4.5.0-0ubuntu4.1 (using .../libqt4-qt3support_4.5.0-0ubuntu4.2_i386.deb) ...
Unpacking replacement libqt4-qt3support ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libqt4-qt3support_4.5.0-0ubuntu4.2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/qt4/plugins/designer/libqt3supportwidgets.so')
Preparing to replace sun-java6-bin 6-14-0ubuntu1.9.04 (using .../sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/i386/client/libjvm.so')
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-qt3support_4.5.0-0ubuntu4.2_i386.deb
 /var/cache/apt/archives/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ahbart on 2009-09-11
You could try:
```
sudo apt-get clean
```

---

### Post by veggiefish on 2009-09-11
thanks- that is now letting me download the broken packages, so should work! :)

---

