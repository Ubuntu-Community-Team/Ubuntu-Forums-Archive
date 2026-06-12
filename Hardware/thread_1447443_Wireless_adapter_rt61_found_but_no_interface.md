---
title: "Wireless adapter rt61 found but no interface"
date: 2010-04-05
forum: Hardware
---

### Post by nukemonk on 2010-04-05
Hello,
 
I've been searching the net for a while to get wifi working on my laptop running Ubuntu 9.10. When I run the lspci command I get the following output:
[FONT=Courier New][SIZE=3]05:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g[/SIZE][/FONT]
 
[FONT=Courier New]I guess Ubuntu does have drivers for my wireless adapter installed.[/FONT]
[FONT=Courier New]The problem now is that I dont have a wireless interface. I've tried compiling rt61 drivers myself but without succes. When running the "make all" command I get this:[/FONT]
[FONT=Courier New][FONT=Courier New][SIZE=3]make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/rick/rt61/Module modules[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]scripts/Makefile.build:49: *** CFLAGS was changed in "/home/rick/rt61/Module/Makefile". Fix it to use EXTRA_CFLAGS. Stop.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]make[1]: *** [_module_/home/rick/rt61/Module] Error 2[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]make: *** [all] Error 2[/FONT][/SIZE]
 
[FONT=Courier New]I've also tried installing windows driver using ndiswrapper. No succes either.[/FONT]
[FONT=Courier New]Is there anyone familliar with this problem?[/FONT]
[/FONT]

---

