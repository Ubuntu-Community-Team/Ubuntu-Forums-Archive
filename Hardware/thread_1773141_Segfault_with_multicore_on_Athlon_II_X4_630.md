---
title: "Segfault with multicore on Athlon II X4 630"
date: 2011-06-01
forum: Hardware
---

### Post by gene02 on 2011-06-01
I am having trouble getting my new 4 core CPU working without segfaults.  Here's the full story:

I've just built a new machine with these parts:

AMD Athlon II X4 630 2.8Ghz
MSI 870-G45 AM3 Motherboard
Athlon II X4 630 3.8GHz CPU
Mushkin 3x2GB DDR3 SDRAM 1333 (PC3 10666)
Zotac GeForce 8400 PCI Express 2.0 x16 HDCP Video Card

And I'm running Lucid (Ubuntu 10.04.2 LTS).

I found when first starting this system up, that only 1 of the 4 Athlon cores was being seen by the machine as reported by /proc/cpuinfo, and as seen in this dmesg line:
```
kernel: [    0.065340] Brought up 1 CPUs
kernel: [    0.743748] powernow-k8: Found 1 AMD Athlon(tm) II X4 630 Processor processors (1 cpu cores) (version 2.20.00)

```
So I tried tinkering with my grub boot command.  Originally it was this:
```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-server root=UUID=60fdfdb6-9c43-4815-90a4-2caae57b8ef8 ro pci=noacpi noacpi noapci nolapic splash

```
I took out the "nolapic", leaving me with this:
```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-server root=UUID=60fdfdb6-9c43-4815-90a4-2caae57b8ef8 ro pci=noacpi noacpi noapci splash

```
That was a triumph.  I had all 4 cores coming up:
```
kernel: [    0.660020] Brought up 4 CPUs
kernel: [    1.187752] powernow-k8: Found 1 AMD Athlon(tm) II X4 630 Processor processors (4 cpu cores) (version 2.20.00)

```
However, within 30 minutes to an hour of booting, I started seeing segfaults all over the place:

```
Jun  1 05:10:01 howler kernel: [23767.244009] apache_processe[16198]: segfault at 3 ip 00007feb2ede5cf7 sp 00007fffb4ce0de8 error 6 in libc-2.11.1.so[7feb2ed5f000+17a000]
Jun  1 05:10:01 howler kernel: [23767.477967] apache_accesses[16203]: segfault at 110200000012 ip 00007f9f4cae747b sp 00007ffff8df1590 error 4 in libperl.so.5.10.1[7f9f4ca1e000+162000]
Jun  1 05:10:01 howler kernel: [23767.585198] apache_accesses[16204]: segfault at 440d0000000a ip 00007fe5ba3a59d4 sp 00007fffea8572a0 error 6 in libperl.so.5.10.1[7fe5ba2f3000+162000]
Jun  1 05:10:01 howler kernel: [23767.622224] munin-node[16194] general protection ip:7f9ce19b1b4b sp:7fff9f00e020 error:0 in libperl.so.5.10.1[7f9ce1908000+162000]
Jun  1 05:10:11 howler kernel: [23777.071886] munin-graph[16247]: segfault at 883f4c0 ip 00007f487e8b7443 sp 00007fffbb3260d0 error 4 in libperl.so.5.10.1[7f487e841000+162000]
[...]
Jun  1 05:14:09 howler kernel: [24015.656720] qpsmtpd-forkser[16263]: segfault at b00000009 ip 00007f77e45c6eb4 sp 00007fff89b0dd50 error 4 in libperl.so.5.10.1[7f77e451c000+162000]
Jun  1 05:14:44 howler kernel: [24050.674149] megaclisas-stat[16267]: segfault at 8 ip 00000000004d5f4e sp 00007fff5c3dbb88 error 6 in python2.6[400000+21c000]
[...]
Jun  1 05:20:02 howler kernel: [24368.223450] apache_accesses[16352]: segfault at 0 ip 00007f9ffc8c0b6a sp 00007fff95aedda0 error 4 in libperl.so.5.10.1[7f9ffc81c000+162000]
Jun  1 05:20:03 howler kernel: [24369.365336] weather_94107[16502]: segfault at ac ip 000000000046a048 sp 00007fff3a978fb0 error 4 in python2.6[400000+21c000]
Jun  1 05:20:03 howler kernel: [24369.438951] weather_94107[16503]: segfault at ac ip 00000000004d5ce8 sp 00007fff31339d40 error 4 in python2.6[400000+21c000]

```

This has happened consistently through three reboots.  I finally went back and put "nolapic" in the grub boot command, and the segfaults have gone away -- along with 3 of my 4 cores.  Does anyone have any advice on what I can try?


SOLVED: Problem == Bad RAM

---

### Post by gene02 on 2011-06-07
Problem == bad RAM

---

