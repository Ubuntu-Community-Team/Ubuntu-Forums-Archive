---
title: "Brother MFC-6490-CW scanner won't work Ubuntu 16.04"
date: 2018-01-29
forum: Hardware
---

### Post by michael337 on 2018-01-29
I've been trying to install the scanner + scanner package binary from [http://download.brother.com/welcome/dlf006893/linux-brprinter-installer-2.2.0-1.gz](http://download.brother.com/welcome/dlf006893/linux-brprinter-installer-2.2.0-1.gz)
but only the printing functionality is working, but the scanner function doesn't.
Here is a dpkg log of the driver installing ```
2018-01-28 16:34:51 status installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:52 remove mfc6490cwcupswrapper:i386 1.1.2-2 <none>
2018-01-28 16:34:52 status half-configured mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:52 status half-installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:52 status config-files mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:52 status config-files mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:53 status config-files mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:53 status not-installed mfc6490cwcupswrapper:i386 <none>
2018-01-28 16:34:55 startup archives install
2018-01-28 16:34:56 upgrade mfc6490cwlpr:i386 1.1.2-2 1.1.2-2
2018-01-28 16:34:56 status half-configured mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:56 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:56 status half-installed mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:56 status half-installed mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:56 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:56 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:56 configure mfc6490cwlpr:i386 1.1.2-2 1.1.2-2
2018-01-28 16:34:56 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:57 status half-configured mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:57 status installed mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:34:57 startup archives install
2018-01-28 16:34:57 install mfc6490cwcupswrapper:i386 <none> 1.1.2-2
2018-01-28 16:34:57 status half-installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:58 status unpacked mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:58 status unpacked mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:58 configure mfc6490cwcupswrapper:i386 1.1.2-2 1.1.2-2
2018-01-28 16:34:58 status unpacked mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:34:58 status half-configured mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:35:11 status installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:41:54 startup archives install
2018-01-28 16:41:55 upgrade brscan3:amd64 0.2.13-1 0.2.13-1
2018-01-28 16:41:55 status half-configured brscan3:amd64 0.2.13-1
2018-01-28 16:41:55 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:41:55 status half-installed brscan3:amd64 0.2.13-1
2018-01-28 16:41:55 status half-installed brscan3:amd64 0.2.13-1
2018-01-28 16:41:55 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:41:56 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:41:56 configure brscan3:amd64 0.2.13-1 0.2.13-1
2018-01-28 16:41:56 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:41:56 status half-configured brscan3:amd64 0.2.13-1
2018-01-28 16:41:56 status installed brscan3:amd64 0.2.13-1
2018-01-28 16:41:58 startup archives install
2018-01-28 16:41:58 upgrade brscan-skey:amd64 0.2.4-1 0.2.4-1
2018-01-28 16:41:58 status half-configured brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:58 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:58 status half-installed brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:58 status half-installed brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:59 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:59 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:59 configure brscan-skey:amd64 0.2.4-1 0.2.4-1
2018-01-28 16:41:59 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:59 status half-configured brscan-skey:amd64 0.2.4-1
2018-01-28 16:41:59 status installed brscan-skey:amd64 0.2.4-1
2018-01-28 16:42:55 startup packages purge
2018-01-28 16:42:55 status installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:42:55 remove mfc6490cwcupswrapper:i386 1.1.2-2 <none>
2018-01-28 16:42:55 status half-configured mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:42:56 status half-installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:42:57 status config-files mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:42:57 status config-files mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:42:57 status config-files mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:42:58 status not-installed mfc6490cwcupswrapper:i386 <none>
2018-01-28 16:43:00 startup archives install
2018-01-28 16:43:00 upgrade mfc6490cwlpr:i386 1.1.2-2 1.1.2-2
2018-01-28 16:43:00 status half-configured mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status half-installed mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status half-installed mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 configure mfc6490cwlpr:i386 1.1.2-2 1.1.2-2
2018-01-28 16:43:01 status unpacked mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status half-configured mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:01 status installed mfc6490cwlpr:i386 1.1.2-2
2018-01-28 16:43:02 startup archives install
2018-01-28 16:43:02 install mfc6490cwcupswrapper:i386 <none> 1.1.2-2
2018-01-28 16:43:02 status half-installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:43:02 status unpacked mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:43:02 status unpacked mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:43:03 configure mfc6490cwcupswrapper:i386 1.1.2-2 1.1.2-2
2018-01-28 16:43:03 status unpacked mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:43:03 status half-configured mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:43:18 status installed mfc6490cwcupswrapper:i386 1.1.2-2
2018-01-28 16:44:11 startup archives install
2018-01-28 16:44:11 upgrade brscan3:amd64 0.2.13-1 0.2.13-1
2018-01-28 16:44:11 status half-configured brscan3:amd64 0.2.13-1
2018-01-28 16:44:11 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:44:11 status half-installed brscan3:amd64 0.2.13-1
2018-01-28 16:44:11 status half-installed brscan3:amd64 0.2.13-1
2018-01-28 16:44:12 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:44:12 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:44:12 configure brscan3:amd64 0.2.13-1 0.2.13-1
2018-01-28 16:44:12 status unpacked brscan3:amd64 0.2.13-1
2018-01-28 16:44:12 status half-configured brscan3:amd64 0.2.13-1
2018-01-28 16:44:12 status installed brscan3:amd64 0.2.13-1
2018-01-28 16:44:12 startup archives install
2018-01-28 16:44:13 upgrade brscan-skey:amd64 0.2.4-1 0.2.4-1
2018-01-28 16:44:13 status half-configured brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status half-installed brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status half-installed brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 configure brscan-skey:amd64 0.2.4-1 0.2.4-1
2018-01-28 16:44:13 status unpacked brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status half-configured brscan-skey:amd64 0.2.4-1
2018-01-28 16:44:13 status installed brscan-skey:amd64 0.2.4-1
2018-01-28 16:48:28 startup archives install
2018-01-28 16:48:29 install ia32-libs:amd64 <none> 1:0.4
2018-01-28 16:48:29 status half-installed ia32-libs:amd64 1:0.4
2018-01-28 16:48:29 status unpacked ia32-libs:amd64 1:0.4
2018-01-28 16:48:29 status unpacked ia32-libs:amd64 1:0.4
2018-01-28 16:50:14 startup archives install
2018-01-28 16:51:05 startup archives install
2018-01-28 16:51:06 install ia32-libs-i386:i386 <none> 1:0.4
2018-01-28 16:51:06 status half-installed ia32-libs-i386:i386 1:0.4
2018-01-28 16:51:06 status unpacked ia32-libs-i386:i386 1:0.4
2018-01-28 16:51:06 status unpacked ia32-libs-i386:i386 1:0.4
2018-01-28 16:52:30 startup packages remove
2018-01-28 16:52:30 status unpacked ia32-libs:amd64 1:0.4
2018-01-28 16:52:30 remove ia32-libs:amd64 1:0.4 <none>
2018-01-28 16:52:30 status half-installed ia32-libs:amd64 1:0.4
2018-01-28 16:52:31 status config-files ia32-libs:amd64 1:0.4
2018-01-28 16:52:31 status config-files ia32-libs:amd64 1:0.4
2018-01-28 16:52:31 status config-files ia32-libs:amd64 1:0.4
2018-01-28 16:52:31 status not-installed ia32-libs:amd64 <none>
2018-01-28 16:52:31 status unpacked ia32-libs-i386:i386 1:0.4
2018-01-28 16:52:31 remove ia32-libs-i386:i386 1:0.4 <none>
2018-01-28 16:52:31 status half-installed ia32-libs-i386:i386 1:0.4
2018-01-28 16:52:31 status config-files ia32-libs-i386:i386 1:0.4
2018-01-28 16:52:31 status config-files ia32-libs-i386:i386 1:0.4
2018-01-28 16:52:31 status config-files ia32-libs-i386:i386 1:0.4
2018-01-28 16:52:31 status not-installed ia32-libs-i386:i386 <none>
2018-01-28 16:52:32 startup packages configure
```
The scanner driver worked on a previous installation that was upgraded from 14.04 to 16.04, but it's gone. The most possible reason why the scanner doesn't work is because some dependencies aren't installed.
I thought that the dependency was ia32-libs, I was trying to install ia32-libs, because it said that it wasn't  installed, but I gave up, because it has so many dependencies that don't  exist on repositories.
Is there a way how to configure the scanner driver correctly?
I'm using ubuntu 16.04

---

### Post by michael337 on 2018-01-29
bump, is there a way how to fix this?

---

### Post by pdc on 2018-01-29
I would suggest you try using the Brother Installer Tool; 

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

the above FAQ page from Brother; on scanners; shows various "Oh, by the way .............." things that seem to be needed; I suspect the Installer Tool is up with them all  ............eg having libusb ............ copying the various files ....... installing the udev permissions file etc etc

---

