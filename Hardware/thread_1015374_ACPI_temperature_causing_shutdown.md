---
title: "ACPI temperature causing shutdown"
date: 2008-12-18
forum: Hardware
---

### Post by henkeb on 2008-12-18
Hi guys. A couple of days ago after working perfectly for quite some time, my laptop started shutting down randomly. After some research I have concluded that acpi is probably the reason. Somehow the CPU temperature is misread, if I check using acpi -V it says temp. is around 45 C, a couple of minutes or seconds later computer shuts down and when I check syslog it shows some error message about temp. being 146 C. I have disabled acpi and it seems to do the trick so far, but I don't want to have to disable it to be able to use my computer. I have seen a couple of others with the same problem but no solution so far. Please help, this is really annoying. Here is output from cat /var/log/syslog | grep shutting:

Dec 16 20:10:34 henrik-laptop kernel: [  571.989784] Critical temperature reached (146 C), shutting down.
Dec 16 20:10:36 henrik-laptop kernel: [  573.990783] Critical temperature reached (146 C), shutting down.
Dec 16 20:10:38 henrik-laptop kernel: [  575.989896] Critical temperature reached (146 C), shutting down.
Dec 16 20:10:40 henrik-laptop kernel: [  578.005882] Critical temperature reached (146 C), shutting down.
Dec 16 20:10:42 henrik-laptop kernel: [  580.027971] Critical temperature reached (146 C), shutting down.
Dec 17 08:55:44 henrik-laptop kernel: [  190.816823] Critical temperature reached (146 C), shutting down.
Dec 17 08:55:46 henrik-laptop kernel: [  192.819738] Critical temperature reached (42 C), shutting down.
Dec 17 08:59:44 henrik-laptop kernel: [  175.805952] Critical temperature reached (146 C), shutting down.
Dec 17 08:59:46 henrik-laptop kernel: [  177.817830] Critical temperature reached (146 C), shutting down.
Dec 17 08:59:48 henrik-laptop kernel: [  179.805917] Critical temperature reached (146 C), shutting down.
Dec 17 08:59:50 henrik-laptop kernel: [  181.817842] Critical temperature reached (146 C), shutting down.
Dec 17 09:13:04 henrik-laptop kernel: [  716.001962] Critical temperature reached (146 C), shutting down.
Dec 17 09:13:06 henrik-laptop kernel: [  717.990862] Critical temperature reached (146 C), shutting down.
Dec 17 09:13:08 henrik-laptop kernel: [  720.003265] Critical temperature reached (146 C), shutting down.
Dec 17 09:13:10 henrik-laptop kernel: [  722.001842] Critical temperature reached (146 C), shutting down.
Dec 17 09:23:15 henrik-laptop kernel: [  566.001928] Critical temperature reached (146 C), shutting down.
Dec 17 09:23:17 henrik-laptop kernel: [  568.001837] Critical temperature reached (146 C), shutting down.
Dec 17 09:23:19 henrik-laptop kernel: [  570.005907] Critical temperature reached (146 C), shutting down.
Dec 17 09:23:21 henrik-laptop kernel: [  572.001857] Critical temperature reached (146 C), shutting down.
Dec 17 16:06:41 henrik-laptop kernel: [  175.817930] Critical temperature reached (146 C), shutting down.
Dec 17 16:06:43 henrik-laptop kernel: [  177.806915] Critical temperature reached (146 C), shutting down.
Dec 17 16:06:45 henrik-laptop kernel: [  179.805908] Critical temperature reached (146 C), shutting down.
Dec 17 16:06:47 henrik-laptop kernel: [  181.805920] Critical temperature reached (146 C), shutting down.
Dec 17 16:27:52 henrik-laptop kernel: [ 1201.001942] Critical temperature reached (146 C), shutting down.
Dec 17 16:27:54 henrik-laptop kernel: [ 1203.001886] Critical temperature reached (146 C), shutting down.
Dec 17 16:27:56 henrik-laptop kernel: [ 1205.001899] Critical temperature reached (146 C), shutting down.
Dec 17 16:41:47 henrik-laptop kernel: [  806.001929] Critical temperature reached (146 C), shutting down.
Dec 17 16:41:49 henrik-laptop kernel: [  807.990861] Critical temperature reached (146 C), shutting down.
Dec 17 16:41:51 henrik-laptop kernel: [  810.024087] Critical temperature reached (146 C), shutting down.
Dec 17 16:41:53 henrik-laptop kernel: [  811.990872] Critical temperature reached (146 C), shutting down.
Dec 17 17:36:53 henrik-laptop kernel: [ 2347.001877] Critical temperature reached (146 C), shutting down.
Dec 17 17:36:55 henrik-laptop kernel: [ 2349.001864] Critical temperature reached (146 C), shutting down.
Dec 17 17:36:57 henrik-laptop kernel: [ 2350.993286] Critical temperature reached (146 C), shutting down.
Dec 17 17:36:59 henrik-laptop kernel: [ 2352.989908] Critical temperature reached (146 C), shutting down.
Dec 17 17:47:21 henrik-laptop kernel: [  595.001170] Critical temperature reached (146 C), shutting down.
Dec 17 17:47:23 henrik-laptop kernel: [  597.005904] Critical temperature reached (146 C), shutting down.
Dec 17 17:47:25 henrik-laptop kernel: [  599.001898] Critical temperature reached (146 C), shutting down.
Dec 17 17:47:27 henrik-laptop kernel: [  601.001951] Critical temperature reached (146 C), shutting down.
Dec 17 17:49:29 henrik-laptop kernel: [   89.274444] Critical temperature reached (146 C), shutting down.
Dec 17 17:49:31 henrik-laptop kernel: [   91.817878] Critical temperature reached (146 C), shutting down.
Dec 17 17:49:33 henrik-laptop kernel: [   93.805917] Critical temperature reached (146 C), shutting down.
Dec 17 20:50:50 henrik-laptop kernel: [ 5510.988795] Critical temperature reached (146 C), shutting down.
Dec 17 20:50:52 henrik-laptop kernel: [ 5512.989833] Critical temperature reached (146 C), shutting down.
Dec 17 20:50:54 henrik-laptop kernel: [ 5514.990835] Critical temperature reached (146 C), shutting down.
Dec 17 20:50:56 henrik-laptop kernel: [ 5517.001816] Critical temperature reached (146 C), shutting down.
Dec 17 22:09:07 henrik-laptop kernel: [  114.817834] Critical temperature reached (146 C), shutting down.
Dec 17 22:09:09 henrik-laptop kernel: [  116.817843] Critical temperature reached (146 C), shutting down.
Dec 17 22:09:11 henrik-laptop kernel: [  118.806848] Critical temperature reached (146 C), shutting down.
Dec 17 22:09:13 henrik-laptop kernel: [  120.817924] Critical temperature reached (146 C), shutting down.
Dec 18 13:05:46 henrik-laptop kernel: [   24.676949] Critical temperature reached (146 C), shutting down.
Dec 18 13:05:48 henrik-laptop kernel: [   26.817950] Critical temperature reached (146 C), shutting down.
Dec 18 13:05:50 henrik-laptop kernel: [   28.805950] Critical temperature reached (146 C), shutting down.
Dec 18 23:59:22 henrik-laptop kernel: [ 3945.000959] Critical temperature reached (146 C), shutting down.
Dec 18 23:59:24 henrik-laptop kernel: [ 3947.004887] Critical temperature reached (48 C), shutting down.
Dec 19 00:03:18 henrik-laptop kernel: [  206.817910] Critical temperature reached (146 C), shutting down.
Dec 19 00:03:20 henrik-laptop kernel: [  208.821905] Critical temperature reached (146 C), shutting down.
Dec 19 00:03:22 henrik-laptop kernel: [  210.827653] Critical temperature reached (146 C), shutting down.
Dec 19 00:03:24 henrik-laptop kernel: [  212.817865] Critical temperature reached (146 C), shutting down.
Dec 19 00:23:32 henrik-laptop kernel: [ 1183.000748] Critical temperature reached (146 C), shutting down.
Dec 19 00:23:34 henrik-laptop kernel: [ 1185.004915] Critical temperature reached (52 C), shutting down.

---

### Post by henkeb on 2008-12-19
Anyone?? Is there a way to maybe "downgrade" acpi to an  older version, don't know if I updated it or something cause this problem is completely new to me, never happened in a year until now.

---

