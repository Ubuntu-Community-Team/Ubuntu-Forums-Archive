---
title: "cpu freq reading, ext4 &amp; ssd"
date: 2011-12-21
forum: Hardware
---

### Post by aanti on 2011-12-21
Hi there!

I have a few questions regarding cpu frequency reading and ext4 formatting / mounting options:

i overclocked my cpu (athlon II 640) from 15x200mhz to 15x220mhz:
```
aanti@blackbox:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 5
model name      : AMD Athlon(tm) II X4 640 Processor
stepping        : 3
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save
bogomips        : 6600.35
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```It obviously doesnt recognize the changed frequency as it should be 880 mhz on the x4 multiplier.. But from the Bogomips Value i think the real clock is 220 mhz. Is there a way to read the exact frequency ?


Regarding ssd and ext4:
im not sure if i have the right mount options and if i formatted the drive in the right way:

fstab:
```
# / was on /dev/sda2 during installation
UUID=396b2590-4d3a-488b-89e6-43b2c4646929 /               ext4    noatime,discard,data=ordered,errors=remount-ro 0 1
# /home was on /dev/sda4 during installation
UUID=3b2f066e-d389-48b1-bd8c-dd6ad3acbdde /home           ext4    noatime,discard,data=ordered 0 2
```fdisk -l:
```
Disk /dev/sda: 128.0 GB, 128035676160 bytes                                                                                  
255 Köpfe, 63 Sektoren/Spur, 15566 Zylinder, zusammen 250069680 Sektoren                                                     
Einheiten = Sektoren von 1 × 512 = 512 Bytes                                                                                 
Sector size (logical/physical): 512 bytes / 512 bytes                                                                        
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe491ba47

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System                                                 
/dev/sda1           20480    20600831    10290176   83  Linux
/dev/sda2   *    20600832   215912447    97655808    7  HPFS/NTFS/exFAT
/dev/sda3       215912448   250068991    17078272   83  Linux
```with these settings i get this from a hdparm -Tt /dev/sda:

```
 Timing cached reads:   4026 MB in  2.00 seconds = 2013.15 MB/sec
 Timing buffered disk reads: 752 MB in  3.00 seconds = 250.50 MB/sec
```I wonder if these numbers are okay. On a OpenSuse 11.X installation (just for testing things) i had 390MB/sec in buffered disk reads, but i dont remembern which FS it used..

Are there more verbose benchmarks for linux ?

Oh and this is on 64bit Kubuntu Oneiric..
Linux blackbox 3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by aanti on 2011-12-22
no one ?

---

### Post by aanti on 2011-12-29
come on, nobody uses ubuntu on on a ext4 formatted ssd ?

---

