---
title: "Ubuntu 8.04.1 very slow/unresponsive"
date: 2008-10-12
forum: General Help
---

### Post by riahc3 on 2008-10-12
Why is my Ubuntu 8.04.1 very slow/unresponsive? It freezes and it just generally slow. Anyway how to fix it? It was NEVER like this before.

---

### Post by fabietto0102 on 2008-10-12
Hi,

try to reinstall it. or try other distros. or better, go back to 7.10. I love gutsy gibbon!

---

### Post by Ryadt on 2008-10-12
> **riahc3 said:**
> Why is my Ubuntu 8.04.1 very slow/unresponsive? It freezes and it just generally slow. Anyway how to fix it? It was NEVER like this before.
Can you provide more details.

---

### Post by forger on 2008-10-12
You haven't given any information on your current system and specifications.

Explain what are you doing, when is it slow, while running which applications.. also, check out the output of the command:
```
top
```

---

### Post by riahc3 on 2008-10-12
> **forger said:**
> You haven't given any information on your current system and specifications.

Explain what are you doing, when is it slow, while running which applications.. also, check out the output of the command:
```
top
```

I start it up and its just slow. Windows don't respond. Firefox becomes grey when I switch to another window. If it goes into screensaver mode, it doesnt come out (the cursor freezes and doesnt move at all. Disk activity is just null (every about 2 mins the light comes up and comes down again)

Any other info needed?

---

### Post by Sam on 2008-10-12
Please post the output of the command```
cat /proc/cpuinfo |grep 'model name' && free -m
```

---

### Post by riahc3 on 2008-10-12
Sam:

model name	: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
model name	: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
             total       used       free     shared    buffers     cached
Mem:          2025       1830        195          0        446        698
-/+ buffers/cache:        686       1339
Swap:          953          0        953




Result of top:
top - 03:00:16 up 3 min,  2 users,  load average: 1.99, 1.61, 0.70
Tasks: 128 total,   3 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s): 44.1%us,  7.0%sy,  0.0%ni, 48.2%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   2074536k total,  1713772k used,   360764k free,   456624k buffers
Swap:   976552k total,        0k used,   976552k free,   714992k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6523 user    20   0  333m 311m  12m R   76 15.4   1:38.65 compiz.real        
 5997 root      20   0  825m  29m 8756 S   14  1.5   0:27.00 Xorg               
 6332 user    20   0  7364 4452 1916 S    6  0.2   0:09.34 gconfd-2           
 3845 root      20   0     0    0    0 S    1  0.0   0:00.02 pdflush            
 6573 user    20   0 30976  12m 8840 S    1  0.6   0:00.32 nm-applet          
 6822 user    20   0  137m  50m  20m S    1  2.5   0:06.15 firefox            
 6957 user    20   0 68824  18m  10m R    1  0.9   0:00.62 gnome-terminal     
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
user@user-laptop:~$ cat /proc/cpuinfo |grep 'model name' && free -m
model name	: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
model name	: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
             total       used       free     shared    buffers     cached
Mem:          2025       1830        195          0        446        698
-/+ buffers/cache:        686       1339
Swap:          953          0        953
user@user-laptop:~$ top >top

[1]+  Stopped                 top > top
user@user-laptop:~$ cat top

top - 03:02:18 up 5 min,  2 users,  load average: 1.08, 1.39, 0.73
Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 41.8%us,  7.7%sy,  0.0%ni, 50.2%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2074536k total,  1975632k used,    98904k free,   456788k buffers
Swap:   976552k total,        0k used,   976552k free,   715308k cached
 Unknown command - try 'h' for help 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6523 user    20   0  589m 568m  12m R   72 28.1   3:08.13 compiz.real        
 5997 root      20   0  825m  29m 8760 S   13  1.5   0:43.98 Xorg               
 6332 user    20   0  7364 4452 1916 S    7  0.2   0:17.34 gconfd-2           
 6957 user    20   0 68824  18m  10m S    1  0.9   0:00.80 gnome-terminal     
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1

---

### Post by Sam on 2008-10-12
It seems that compiz slows down the whole system...

---

### Post by OutOfReach on 2008-10-12
Right, try to disable compiz (Appearance>Preferences>Appearance>Visual Effects tab and switch to None)
See if that helps.


Or goto a terminal and type in:
```

metacity --replace &
```

---

### Post by riahc3 on 2008-10-12
But compiz was working great.

I want to fix this, not disable something.

---

### Post by niccholaspage on 2008-10-12
Atleast disable Compiz to see if it is the problem.

---

### Post by forger on 2008-10-13
> **riahc3 said:**
> But compiz was working great.

I want to fix this, not disable something.

the keyword is that it *was* working great :)
something drives compiz nuts apparently

can you post the output of:
```
sudo lshw -short
lspci
top -b -n2
```

Consider filing a bug if you are eager to fix this.. And maybe you haven't noticed, but please in the future be more polite in your posts.. Imperative creates nothing but problems :)

you can file a bug report at [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by riahc3 on 2008-10-14
sudo lshw -short

```

H/W path             Device      Class          Description
===========================================================
                                 system         Vostro1510
/0                               bus            0G914C
/0/1                             memory         107KiB BIOS
/0/5                             processor      Intel(R) Core(TM)2 Duo CPU     T
/0/5/6                           memory         32KiB L1 cache
/0/5/7                           memory         2MiB L2 cache
/0/5/1.1                         processor      Logical CPU
/0/5/1.2                         processor      Logical CPU
/0/11                            memory         2GiB System Memory
/0/11/0                          memory         1GiB SODIMM Synchronous 667 MHz 
/0/11/1                          memory         1GiB SODIMM Synchronous 667 MHz 
/0/0                             processor      
/0/0/1.1                         processor      Logical CPU
/0/0/1.2                         processor      Logical CPU
/0/100                           bridge         Mobile PM965/GM965/GL960 Memory 
/0/100/1                         bridge         Mobile PM965/GM965/GL960 PCI Exp
/0/100/1/0                       display        GeForce 8400M GS
/0/100/1a                        bus            82801H (ICH8 Family) USB UHCI Co
/0/100/1a/1          usb1        bus            UHCI Host Controller
/0/100/1a/1/2                    communication  Bluetooth wireless interface
/0/100/1a.1                      bus            82801H (ICH8 Family) USB UHCI Co
/0/100/1a.1/1        usb2        bus            UHCI Host Controller
/0/100/1a.7                      bus            82801H (ICH8 Family) USB2 EHCI C
/0/100/1a.7/1        usb6        bus            EHCI Host Controller
/0/100/1a.7/1/3                  multimedia     Integrated Webcam
/0/100/1b                        multimedia     82801H (ICH8 Family) HD Audio Co
/0/100/1c                        bridge         82801H (ICH8 Family) PCI Express
/0/100/1c.1                      bridge         82801H (ICH8 Family) PCI Express
/0/100/1c.3                      bridge         82801H (ICH8 Family) PCI Express
/0/100/1c.3/0        wmaster0    network        PRO/Wireless 4965 AG or AGN Netw
/0/100/1c.4                      bridge         82801H (ICH8 Family) PCI Express
/0/100/1c.4/0        eth0        network        RTL8111/8168B PCI Express Gigabi
/0/100/1d                        bus            82801H (ICH8 Family) USB UHCI Co
/0/100/1d/1          usb3        bus            UHCI Host Controller
/0/100/1d.1                      bus            82801H (ICH8 Family) USB UHCI Co
/0/100/1d.1/1        usb4        bus            UHCI Host Controller
/0/100/1d.1/1/1                  generic        USB Gaming Mouse
/0/100/1d.2                      bus            82801H (ICH8 Family) USB UHCI Co
/0/100/1d.2/1        usb5        bus            UHCI Host Controller
/0/100/1d.7                      bus            82801H (ICH8 Family) USB2 EHCI C
/0/100/1d.7/1        usb7        bus            EHCI Host Controller
/0/100/1e                        bridge         82801 Mobile PCI Bridge
/0/100/1e/5                      bus            Firewire (IEEE 1394)
/0/100/1e/5.2                    system         Integrated MMC/SD Controller
/0/100/1e/5.3                    storage        Integrated MS/xD Controller
/0/100/1f                        bridge         82801HEM (ICH8M) LPC Interface C
/0/100/1f.1          scsi3       storage        82801HBM/HEM (ICH8M/ICH8M-E) IDE
/0/100/1f.1/0.0.0    /dev/cdrom  disk           DVD+-RW UJ-875S
/0/100/1f.2          scsi0       storage        82801HBM/HEM (ICH8M/ICH8M-E) SAT
/0/100/1f.2/0.0.0    /dev/sda    disk           160GB ST9160827AS
/0/100/1f.2/0.0.0/1  /dev/sda1   volume         86MiB Windows FAT volume
/0/100/1f.2/0.0.0/2  /dev/sda2   volume         148GiB Windows NTFS volume
/0/100/1f.3                      bus            82801H (ICH8 Family) SMBus Contr
/1                               power          SANYO     06/01/01

```

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

top -b -n2
```

top - 18:12:17 up  1:09,  3 users,  load average: 4.99, 4.30, 2.65
Tasks: 150 total,   6 running, 143 sleeping,   0 stopped,   1 zombie
Cpu(s): 23.4%us,  2.9%sy,  0.1%ni, 68.7%id,  4.4%wa,  0.1%hi,  0.4%si,  0.0%st
Mem:   2074536k total,  2001232k used,    73304k free,   471372k buffers
Swap:   976552k total,        0k used,   976552k free,   898392k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12589 user    20   0 76316  53m 9388 R   44  2.6   4:53.05 gtk-gnash          
12569 user    20   0 60768  37m 9256 S   36  1.8   4:13.23 gtk-gnash          
12574 user    20   0 61756  37m 9204 R   36  1.8   4:14.91 gtk-gnash          
13085 user    20   0 49128  18m  10m R   34  0.9   0:30.78 gtk-gnash          
13064 user    20   0 36048  12m 9144 S   20  0.6   0:16.24 gtk-gnash          
 5923 root      20   0  878m  57m  13m R    4  2.8   3:41.13 Xorg               
13054 user    20   0 47104  15m  10m S    4  0.8   0:03.20 gtk-gnash          
13074 user    20   0 32740  10m 8036 S    4  0.5   0:02.29 gtk-gnash          
13075 user    20   0 34712  11m 8888 S    4  0.5   0:01.23 gtk-gnash          
 6494 user    20   0 69444  34m  10m S    2  1.7   1:21.28 compiz.real        
 7023 user    20   0  205m 106m  23m S    2  5.3   1:33.79 firefox            
13052 user    20   0 42916  12m 9844 S    2  0.6   0:01.66 gtk-gnash          
13053 user    20   0 45312  14m  10m R    2  0.7   0:03.57 gtk-gnash          
13056 user    20   0 47080  15m 9844 S    2  0.8   0:02.63 gtk-gnash          
13070 user    20   0 34688  11m 9176 S    2  0.6   0:01.86 gtk-gnash          
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  139 root      15  -5     0    0    0 S    0  0.0   0:00.10 kseriod            
  181 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
  182 root      20   0     0    0    0 S    0  0.0   0:00.22 pdflush            
  183 root      15  -5     0    0    0 S    0  0.0   0:00.22 kswapd0            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1426 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1427 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 1599 root      15  -5     0    0    0 S    0  0.0   0:00.32 ata/0              
 1602 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/1              
 1603 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt           
 1619 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
 2322 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0        
 2363 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
 2364 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
 2365 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
 2446 root      15  -5     0    0    0 S    0  0.0   0:00.98 scsi_eh_3          
 2447 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4          
 2628 root      20   0  8160 5636  620 S    0  0.3   0:19.68 mount.ntfs         
 2664 root       0 -20     0    0    0 S    0  0.0   0:00.68 loop0              
 2666 root      15  -5     0    0    0 S    0  0.0   0:00.10 kjournald          
 2870 root      16  -4  2520 1040  380 S    0  0.1   0:00.40 udevd              
 3267 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused          
 3311 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd              
 4028 root      15  -5     0    0    0 S    0  0.0   0:00.06 iwl4965/0          
 4033 root      15  -5     0    0    0 S    0  0.0   0:00.00 iwl4965/1          
 4196 root      15  -5     0    0    0 S    0  0.0   0:00.10 iwl4965            
 4404 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn          
 4405 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn          
 5033 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty              
 5034 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5036 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5038 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5040 root      20   0  1716  504  440 S    0  0.0   0:00.00 getty              
 5224 root      20   0  2456 1356  692 S    0  0.1   0:00.00 acpid              
 5264 root      15  -5     0    0    0 S    0  0.0   0:00.38 kondemand/0        
 5265 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1        
 5342 syslog    20   0  1936  684  532 S    0  0.0   0:00.04 syslogd            
 5395 root      20   0  1872  532  444 S    0  0.0   0:00.06 dd                 
 5397 klog      20   0  3840 2748  424 S    0  0.1   0:00.12 klogd              
 5419 messageb  20   0  2984 1488  796 S    0  0.1   0:00.74 dbus-daemon        
 5435 root      20   0 30432 2348 1952 S    0  0.1   0:00.62 NetworkManager     
 5449 root      20   0  3536 1324 1128 S    0  0.1   0:00.02 NetworkManagerD    
 5462 root      20   0  4424 2220 1780 S    0  0.1   0:00.04 system-tools-ba    
 5482 avahi     20   0  2892 1468 1212 S    0  0.1   0:00.36 avahi-daemon       
 5483 avahi     20   0  2760  468  288 S    0  0.0   0:00.00 avahi-daemon       
 5525 root      20   0  6048 2508 1900 S    0  0.1   0:00.00 cupsd              
 5659 root      20   0  2020  988  780 S    0  0.0   0:00.16 dhcdbd             
 5685 haldaemo  20   0  6340 4364 3604 S    0  0.2   0:01.96 hald               
 5688 root      20   0  8908 2404 1628 S    0  0.1   0:00.06 console-kit-dae    
 5689 root      20   0  3352 1164  976 S    0  0.1   0:00.26 hald-runner        
 5762 root      20   0  5168 2096 1892 S    0  0.1   0:00.00 hald-addon-dell    
 5763 root      20   0  3416 1152 1004 S    0  0.1   0:00.04 hald-addon-inpu    
 5767 root      20   0  3428 1228 1072 S    0  0.1   0:00.00 hald-addon-cpuf    
 5768 haldaemo  20   0  2204  908  780 S    0  0.0   0:00.00 hald-addon-acpi    
 5792 root      20   0  3420 1140  988 S    0  0.1   0:01.14 hald-addon-stor    
 5815 root      20   0  3172 1316 1136 S    0  0.1   0:00.00 hcid               
 5826 root      20   0  3084 1308 1156 S    0  0.1   0:00.00 bluetoothd-serv    
 5827 root      20   0  3020 1112  976 S    0  0.1   0:00.00 bluetoothd-serv    
 5838 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd           
 5916 root      20   0 14048 1592  964 S    0  0.1   0:00.00 gdm                
 5919 root      20   0 14512 2988 2204 S    0  0.1   0:00.04 gdm                
 5992 daemon    20   0  1984  424  300 S    0  0.0   0:00.00 atd                
 6008 root      20   0  2104  884  712 S    0  0.0   0:00.00 cron               
 6173 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty              
 6308 user    20   0  7356 4448 1916 S    0  0.2   0:01.36 gconfd-2           
 6310 user    20   0 14340 2052 1656 S    0  0.1   0:00.01 gnome-keyring-d    
 6311 user    20   0 28740 7168 6016 S    0  0.3   0:00.18 x-session-manag    
 6390 user    20   0 22956 6736 4884 S    0  0.3   0:00.14 seahorse-agent     
 6394 user    20   0  2828 1212  792 S    0  0.1   0:00.12 dbus-daemon        
 6395 user    20   0 44604  13m 8700 S    0  0.7   0:01.92 gnome-settings-    
 6399 user    20   0 26840 4072 3280 S    0  0.2   0:02.12 pulseaudio         
 6404 user    20   0  5776 2260 1848 S    0  0.1   0:00.00 gconf-helper       
 6419 user    20   0  1772  536  436 S    0  0.0   0:00.00 compiz             
 6420 user    20   0 15332 2820 1848 S    0  0.1   0:13.62 gnome-screensav    
 6421 user    20   0 52056  24m  14m S    0  1.2   0:21.55 gnome-panel        
 6423 user    20   0 83588  35m  16m S    0  1.7   0:12.25 nautilus           
 6427 user    20   0 41148 3300 2448 S    0  0.2   0:00.16 bonobo-activati    
 6453 user    20   0  5372 2120 1800 S    0  0.1   0:00.02 gvfsd              
 6468 user    20   0 29048 1980 1592 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 6499 user    20   0 22284 8556 6224 S    0  0.4   0:00.30 bluetooth-apple    
 6502 user    20   0 33192  14m 9788 S    0  0.7   0:00.46 update-notifier    
 6505 user    20   0 15340 5576 4704 S    0  0.3   0:00.04 tracker-applet     
 6506 user    20   0 63224 9.9m 8468 S    0  0.5   0:00.08 evolution-alarm    
 6508 user    20   0 46268  10m 9144 S    0  0.5   0:00.20 hidpoint-1.0       
 6510 user    39  19 31508  10m 2284 S    0  0.5   0:00.04 trackerd           
 6548 user    20   0 34004  15m  10m S    0  0.8   0:03.74 nm-applet          
 6549 user    20   0 24264  11m 7156 S    0  0.6   0:00.16 python             
 6550 user    20   0 20556 4856 3692 S    0  0.2   0:00.06 gnome-volume-ma    
 6552 user    20   0 28792  10m 6824 S    0  0.5   0:00.56 gnome-power-man    
 6589 user    20   0  5372 2140 1844 S    0  0.1   0:00.00 gvfsd-burn         
 6598 user    20   0 67976 6636 5272 S    0  0.3   0:00.03 evolution-data-    
 6641 user    20   0  4772 1792 1572 S    0  0.1   0:00.02 obex-data-serve    
 6645 user    20   0 27152  13m 7376 S    0  0.6   0:01.12 notification-da    
 6653 user    20   0 13836 2668 2228 S    0  0.1   0:00.01 gvfsd-trash        
 6658 user    20   0 30620 9360 7760 S    0  0.5   0:00.06 evolution-excha    
 6671 user    20   0 29832  13m 9100 S    0  0.7   0:00.34 trashapplet        
 6695 user    20   0  1772  480  416 S    0  0.0   0:00.00 sh                 
 6696 user    20   0 21512  12m 7532 S    0  0.6   0:05.76 gtk-window-deco    
 6703 user    20   0 47884  14m 9796 S    0  0.7   0:00.36 mixer_applet2      
 6711 user    20   0 29704  13m 8832 S    0  0.7   0:00.46 fast-user-switc    
 6714 user    20   0 57024  14m 9868 S    0  0.7   0:00.87 gweather-applet    
 7575 root      20   0 13136  10m 1996 S    0  0.5   0:00.26 SystemToolsBack    
 9206 user    20   0 71172  18m  10m S    0  0.9   0:02.68 gnome-terminal     
 9212 user    20   0  2912  856  708 S    0  0.0   0:00.00 gnome-pty-helpe    
 9213 user    20   0  5704 3120 1412 S    0  0.2   0:00.10 bash               
 9234 root      20   0  4124 1788 1408 S    0  0.1   0:00.04 bash               
11387 ntp       20   0  4136 1232  940 S    0  0.1   0:00.04 ntpd               
11746 user    20   0 46256  30m  10m S    0  1.5   0:00.94 nvidia-settings    
11938 user    20   0  222m  80m  53m S    0  4.0   0:09.04 soffice.bin        
12419 user    20   0  5052 2404  628 S    0  0.1   0:04.80 wineserver         
12422 user    20   0 2586m 2808 2196 S    0  0.1   0:00.00 services.exe       
12424 user    20   0 2584m 3008 2388 S    0  0.1   0:00.00 winedevice.exe     
12431 user    20   0 2592m 7296 5464 S    0  0.4   0:00.68 PnkBstrA.exe       
12440 user    20   0 2587m 6684 5040 S    0  0.3   0:00.30 explorer.exe       
12457 user    20   0 2600m  15m 9.8m S    0  0.8   0:09.33 uTorrent.exe       
12571 user    20   0     0    0    0 Z    0  0.0   0:00.48 gtk-gnash <defunct>
12980 user    20   0  5704 3120 1412 S    0  0.2   0:00.12 bash               
13057 user    20   0 46160  14m  10m S    0  0.7   0:03.22 gtk-gnash          
13138 user    20   0  2304 1032  756 R    0  0.0   0:00.00 top                


top - 18:12:20 up  1:09,  3 users,  load average: 4.91, 4.30, 2.66
Tasks: 150 total,   6 running, 143 sleeping,   0 stopped,   1 zombie
Cpu(s): 92.4%us,  7.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   2074536k total,  2001580k used,    72956k free,   471372k buffers
Swap:   976552k total,        0k used,   976552k free,   898448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12574 user    20   0 61832  37m 9204 R   39  1.8   4:16.09 gtk-gnash          
12589 user    20   0 76396  53m 9388 R   38  2.6   4:54.19 gtk-gnash          
13085 user    20   0 49120  18m  10m R   38  0.9   0:31.92 gtk-gnash          
12569 user    20   0 60828  37m 9256 R   33  1.8   4:14.23 gtk-gnash          
13064 user    20   0 36048  12m 9144 S   18  0.6   0:16.79 gtk-gnash          
 5923 root      20   0  878m  57m  13m S    6  2.8   3:41.32 Xorg               
13053 user    20   0 45312  14m  10m S    4  0.7   0:03.69 gtk-gnash          
13057 user    20   0 46160  14m  10m S    4  0.7   0:03.34 gtk-gnash          
13054 user    20   0 47104  15m  10m S    3  0.8   0:03.29 gtk-gnash          
13074 user    20   0 32740  10m 8036 S    3  0.5   0:02.38 gtk-gnash          
13056 user    20   0 47080  15m 9844 S    2  0.8   0:02.70 gtk-gnash          
 6494 user    20   0 69444  34m  10m S    2  1.7   1:21.33 compiz.real        
 7023 user    20   0  205m 106m  23m S    2  5.3   1:33.84 firefox            
 9206 user    20   0 71348  19m  10m R    1  0.9   0:02.72 gnome-terminal     
13052 user    20   0 42916  12m 9844 S    1  0.6   0:01.70 gtk-gnash          
13075 user    20   0 34712  11m 8888 S    1  0.5   0:01.27 gtk-gnash          
12457 user    20   0 2600m  15m 9.8m S    1  0.8   0:09.36 uTorrent.exe       
13070 user    20   0 34688  11m 9176 S    1  0.6   0:01.89 gtk-gnash          
 5685 haldaemo  20   0  6340 4364 3604 S    1  0.2   0:01.98 hald               
 6421 user    20   0 52056  24m  14m S    1  1.2   0:21.57 gnome-panel        
12419 user    20   0  5052 2404  628 S    1  0.1   0:04.82 wineserver         
12431 user    20   0 2592m 7296 5464 S    1  0.4   0:00.70 PnkBstrA.exe       
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  139 root      15  -5     0    0    0 S    0  0.0   0:00.10 kseriod            
  181 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
  182 root      20   0     0    0    0 S    0  0.0   0:00.22 pdflush            
  183 root      15  -5     0    0    0 S    0  0.0   0:00.22 kswapd0            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1426 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1427 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 1599 root      15  -5     0    0    0 S    0  0.0   0:00.32 ata/0              
 1602 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/1              
 1603 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt           
 1619 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
 2322 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0        
 2363 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
 2364 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
 2365 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
 2446 root      15  -5     0    0    0 S    0  0.0   0:00.98 scsi_eh_3          
 2447 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4          
 2628 root      20   0  8160 5636  620 S    0  0.3   0:19.68 mount.ntfs         
 2664 root       0 -20     0    0    0 S    0  0.0   0:00.68 loop0              
 2666 root      15  -5     0    0    0 S    0  0.0   0:00.10 kjournald          
 2870 root      16  -4  2520 1040  380 S    0  0.1   0:00.40 udevd              
 3267 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused          
 3311 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd              
 4028 root      15  -5     0    0    0 S    0  0.0   0:00.06 iwl4965/0          
 4033 root      15  -5     0    0    0 S    0  0.0   0:00.00 iwl4965/1          
 4196 root      15  -5     0    0    0 S    0  0.0   0:00.10 iwl4965            
 4404 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn          
 4405 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn          
 5033 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty              
 5034 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5036 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5038 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5040 root      20   0  1716  504  440 S    0  0.0   0:00.00 getty              
 5224 root      20   0  2456 1356  692 S    0  0.1   0:00.00 acpid              
 5264 root      15  -5     0    0    0 S    0  0.0   0:00.38 kondemand/0        
 5265 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1        
 5342 syslog    20   0  1936  684  532 S    0  0.0   0:00.04 syslogd            
 5395 root      20   0  1872  532  444 S    0  0.0   0:00.06 dd                 
 5397 klog      20   0  3840 2748  424 S    0  0.1   0:00.12 klogd              
 5419 messageb  20   0  2984 1488  796 S    0  0.1   0:00.74 dbus-daemon        
 5435 root      20   0 30432 2348 1952 S    0  0.1   0:00.62 NetworkManager     
 5449 root      20   0  3536 1324 1128 S    0  0.1   0:00.02 NetworkManagerD    
 5462 root      20   0  4424 2220 1780 S    0  0.1   0:00.04 system-tools-ba    
 5482 avahi     20   0  2892 1468 1212 S    0  0.1   0:00.36 avahi-daemon       
 5483 avahi     20   0  2760  468  288 S    0  0.0   0:00.00 avahi-daemon       
 5525 root      20   0  6048 2508 1900 S    0  0.1   0:00.00 cupsd              
 5659 root      20   0  2020  988  780 S    0  0.0   0:00.16 dhcdbd             
 5688 root      20   0  8908 2404 1628 S    0  0.1   0:00.06 console-kit-dae    
 5689 root      20   0  3352 1164  976 S    0  0.1   0:00.26 hald-runner        
 5762 root      20   0  5168 2096 1892 S    0  0.1   0:00.00 hald-addon-dell    
 5763 root      20   0  3416 1152 1004 S    0  0.1   0:00.04 hald-addon-inpu    
 5767 root      20   0  3428 1228 1072 S    0  0.1   0:00.00 hald-addon-cpuf    
 5768 haldaemo  20   0  2204  908  780 S    0  0.0   0:00.00 hald-addon-acpi    
 5792 root      20   0  3420 1140  988 S    0  0.1   0:01.14 hald-addon-stor    
 5815 root      20   0  3172 1316 1136 S    0  0.1   0:00.00 hcid               
 5826 root      20   0  3084 1308 1156 S    0  0.1   0:00.00 bluetoothd-serv    
 5827 root      20   0  3020 1112  976 S    0  0.1   0:00.00 bluetoothd-serv    
 5838 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd           
 5916 root      20   0 14048 1592  964 S    0  0.1   0:00.00 gdm                
 5919 root      20   0 14512 2988 2204 S    0  0.1   0:00.04 gdm                
 5992 daemon    20   0  1984  424  300 S    0  0.0   0:00.00 atd                
 6008 root      20   0  2104  884  712 S    0  0.0   0:00.00 cron               
 6173 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty              
 6308 user    20   0  7356 4448 1916 S    0  0.2   0:01.36 gconfd-2           
 6310 user    20   0 14340 2052 1656 S    0  0.1   0:00.01 gnome-keyring-d    
 6311 user    20   0 28740 7168 6016 S    0  0.3   0:00.18 x-session-manag    
 6390 user    20   0 22956 6736 4884 S    0  0.3   0:00.14 seahorse-agent     
 6394 user    20   0  2828 1212  792 S    0  0.1   0:00.12 dbus-daemon        
 6395 user    20   0 44604  13m 8700 S    0  0.7   0:01.92 gnome-settings-    
 6399 user    20   0 26840 4072 3280 S    0  0.2   0:02.12 pulseaudio         
 6404 user    20   0  5776 2260 1848 S    0  0.1   0:00.00 gconf-helper       
 6419 user    20   0  1772  536  436 S    0  0.0   0:00.00 compiz             
 6420 user    20   0 15332 2820 1848 S    0  0.1   0:13.62 gnome-screensav    
 6423 user    20   0 83588  35m  16m S    0  1.7   0:12.25 nautilus           
 6427 user    20   0 41148 3300 2448 S    0  0.2   0:00.16 bonobo-activati    
 6453 user    20   0  5372 2120 1800 S    0  0.1   0:00.02 gvfsd              
 6468 user    20   0 29048 1980 1592 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 6499 user    20   0 22284 8556 6224 S    0  0.4   0:00.30 bluetooth-apple    
 6502 user    20   0 33192  14m 9788 S    0  0.7   0:00.46 update-notifier    
 6505 user    20   0 15340 5576 4704 S    0  0.3   0:00.04 tracker-applet     
 6506 user    20   0 63224 9.9m 8468 S    0  0.5   0:00.08 evolution-alarm    
 6508 user    20   0 46268  10m 9144 S    0  0.5   0:00.20 hidpoint-1.0       
 6510 user    39  19 31508  10m 2284 S    0  0.5   0:00.04 trackerd           
 6548 user    20   0 34004  15m  10m S    0  0.8   0:03.74 nm-applet          
 6549 user    20   0 24264  11m 7156 S    0  0.6   0:00.16 python             
 6550 user    20   0 20556 4856 3692 S    0  0.2   0:00.06 gnome-volume-ma    
 6552 user    20   0 28792  10m 6824 S    0  0.5   0:00.56 gnome-power-man    
 6589 user    20   0  5372 2140 1844 S    0  0.1   0:00.00 gvfsd-burn         
 6598 user    20   0 67976 6636 5272 S    0  0.3   0:00.03 evolution-data-    
 6641 user    20   0  4772 1792 1572 S    0  0.1   0:00.02 obex-data-serve    
 6645 user    20   0 27152  13m 7376 S    0  0.6   0:01.12 notification-da    
 6653 user    20   0 13836 2668 2228 S    0  0.1   0:00.01 gvfsd-trash        
 6658 user    20   0 30620 9360 7760 S    0  0.5   0:00.06 evolution-excha    
 6671 user    20   0 29832  13m 9100 S    0  0.7   0:00.34 trashapplet        
 6695 user    20   0  1772  480  416 S    0  0.0   0:00.00 sh                 
 6696 user    20   0 21512  12m 7532 S    0  0.6   0:05.76 gtk-window-deco    
 6703 user    20   0 47884  14m 9796 S    0  0.7   0:00.36 mixer_applet2      
 6711 user    20   0 29704  13m 8832 S    0  0.7   0:00.46 fast-user-switc    
 6714 user    20   0 57024  14m 9868 S    0  0.7   0:00.87 gweather-applet    
 7575 root      20   0 13136  10m 1996 S    0  0.5   0:00.26 SystemToolsBack    
 9212 user    20   0  2912  856  708 S    0  0.0   0:00.00 gnome-pty-helpe    
 9213 user    20   0  5704 3120 1412 S    0  0.2   0:00.10 bash               
 9234 root      20   0  4124 1788 1408 S    0  0.1   0:00.04 bash               
11387 ntp       20   0  4136 1232  940 S    0  0.1   0:00.04 ntpd               
11746 user    20   0 46256  30m  10m S    0  1.5   0:00.94 nvidia-settings    
11938 user    20   0  222m  80m  53m S    0  4.0   0:09.04 soffice.bin        
12422 user    20   0 2586m 2808 2196 S    0  0.1   0:00.00 services.exe       
12424 user    20   0 2584m 3008 2388 S    0  0.1   0:00.00 winedevice.exe     
12440 user    20   0 2587m 6684 5040 S    0  0.3   0:00.30 explorer.exe       
12571 user    20   0     0    0    0 Z    0  0.0   0:00.48 gtk-gnash <defunct>
12980 user    20   0  5704 3120 1412 S    0  0.2   0:00.12 bash               
13138 user    20   0  2312 1132  844 R    0  0.1   0:00.00 top


```

---

### Post by forger on 2008-10-14
Are you using gnash for flash movies on the internet (i.e. youtube)?
In that case, you might want to purge/remove the **gnash** package, it's stable, but can crash on newer flash movies
> Gnash is based on GameSWF, and supports most SWF v7 features and some SWF v8 and v9.

I suggest using flashplugin-nonfree for your flash movies

---

### Post by riahc3 on 2008-10-17
> **forger said:**
> Are you using gnash for flash movies on the internet (i.e. youtube)?
In that case, you might want to purge/remove the **gnash** package, it's stable, but can crash on newer flash movies


I suggest using flashplugin-nonfree for your flash movies

I installed all the flash plugins because they did not work. Thats another topic/issue.

---

