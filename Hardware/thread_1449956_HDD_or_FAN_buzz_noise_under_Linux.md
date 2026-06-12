---
title: "HDD or FAN buzz noise under Linux"
date: 2010-04-08
forum: Hardware
---

### Post by fedemw on 2010-04-08
Hi team,

My Laptop (Toshiba Satellite - U300) is producing an strange noise during activity under Linux (not with Windows XP). I tried shutting down speakers, mic input, changing desktop colors, etc... but no lucky.

This is making me weird... Is there any solution for this? It happens from the moment the OS is loading until I shut this down... not when the computer is on BIOS bootup.

Reading at Google this is normally caused by HDD activity (even if this without an specific work to do). Basically the noise is not the typical read in... and even the ticks described here [(http://ubuntuforums.org/showthread.php?t=710443]((http://ubuntuforums.org/showthread.php?t=710443)).


**· HARDWARE DETAILS:**

```
    lspci
    00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
    00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
    00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
    00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
    00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
    00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
    00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
    00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
    00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
    00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
    00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
    00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
    04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
    0a:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
    0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


    cat /proc/asound/cards
    0 [Intel ]: HDA-Intel - HDA Intel
    HDA Intel at 0xf0800000 irq 22

inxi -plu
Partition: ID:/ size: 23G used: 3.8G (18%) fs: ext4 dev: /dev/sda1 label: N/A uuid: 245a77a0-7273-4710-b3a9-a59e94c96e25
           ID:/var/lib/ureadahead/debugfs size: 23G used: 3.8G (18%) fs: debugfs dev: N/A label: N/A uuid: N/A
           ID:/home size: 115G used: 17G (16%) fs: ext4 dev: /dev/sda2 label: N/A uuid: 3684d37d-66c7-4143-b166-41cb5bea8ee2
           ID:/windows size: 38G used: 32K (1%) fs: vfat dev: /dev/sda3 label: N/A uuid: 5AEC-5CC3
           ID:/disk1 size: 54G used: 19M (1%) fs: vfat dev: /dev/sda5 label: N/A uuid: FDF4-6AC6
           ID:swap-1 size: 3.06GB used: 0.00GB (0%) fs: swap dev: /dev/sda6 label: N/A uuid: c9629951-ca27-422f-b11a-eff79e2efb0a 
```


Thanks in advance for your help team. 

Best,

:guitar:

---

### Post by ajgreeny on 2010-04-08
Run ```
top
``` while it's making the noise and see what is the top process running.

It may give some clues.  But noises are always worrying, aren't they?

---

### Post by fedemw on 2010-04-09
Hi,

thanks for your answer.

See below:

```
top - 10:16:02 up 21:34,  3 users,  load average: 0.49, 0.43, 0.27
Tasks: 189 total,   1 running, 187 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.2%us,  1.5%sy,  0.0%ni, 93.1%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2052492k total,  1836896k used,   215596k free,   100672k buffers
Swap:  2988048k total,    22184k used,  2965864k free,   834368k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
12164 renton    20   0  367m 160m  28m S    5  8.0   0:38.62 firefox-bin                                                                                     
 4566 root      20   0  116m  43m  17m S    2  2.2  21:44.82 Xorg                                                                                            
10113 renton    20   0 41824  13m 9864 S    2  0.7   0:01.99 gnome-terminal                                                                                  
   22 root      15  -5     0    0    0 S    0  0.0   0:04.80 ata/0                                                                                           
 1037 renton    20   0  154m  77m  29m S    0  3.9   0:40.08 acroread                                                                                        
 7637 renton    20   0  292m 149m  81m S    0  7.4   6:28.21 soffice.bin                                                                                     
10013 renton    20   0 55992  21m  12m S    0  1.1   0:39.88 xchat                                                                                           
12822 renton    20   0  2472 1212  884 R    0  0.1   0:00.11 top                                                                                             
19222 renton    20   0  276m 125m  26m S    0  6.3   4:38.77 thunderbird-bin                                                                                 
    1 root      20   0  2664 1476 1128 S    0  0.1   0:01.11 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.76 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.48 events/0                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                          
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns                                                                                           
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                       
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                   
   17 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0                                                                                       
   19 root      15  -5     0    0    0 S    0  0.0   0:00.30 kacpid                                                                                          
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                   
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
   26 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
   27 root      15  -5     0    0    0 S    0  0.0   0:00.05 kseriod                                                                                         
   28 root      15  -5     0    0    0 S    0  0.0   0:00.02 kmmcd                                                                                           
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 bluetooth                                                                                       
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                      
   31 root      20   0     0    0    0 S    0  0.0   0:00.05 pdflush                                                                                         
   32 root      20   0     0    0    0 S    0  0.0   0:00.18 pdflush                                                                                         
   33 root      15  -5     0    0    0 S    0  0.0   0:00.42 kswapd0                                                                                         
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0   
```

---

### Post by ajgreeny on 2010-04-09
Nothing unusual there as far as I can see, but I wonder what the **ata/0** is, that is 4th in the listed processes.

---

### Post by fedemw on 2010-04-12
> **ajgreeny said:**
> Nothing unusual there as far as I can see, but I wonder what the **ata/0** is, that is 4th in the listed processes.

What can I do with that?

Thanks,

---

