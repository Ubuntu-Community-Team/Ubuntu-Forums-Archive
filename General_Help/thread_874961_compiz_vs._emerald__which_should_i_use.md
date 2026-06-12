---
title: "compiz vs. emerald ? which should i use ?"
date: 2008-07-30
forum: General Help
---

### Post by smooth3006 on 2008-07-30
i am using both right now but i noticed the graphical interface seems a bit slow when first starting ubuntu. i do have a good graphics card and had envy install the latest drivers.

---

### Post by anotherdisciple on 2008-07-30
Emerald is a window decorator that requires Compiz to run. So if you want to keep using emerald... you have to use Compiz.

---

### Post by Victormd on 2008-07-30
Compiz and emerald are different things. Compiz is a composite manager, and emerald is a windows decorator that requires compiz to work. It's well known that compiz slows your comp. down a bit during startup but once it's loaded, you barely notice it. However, there are a few tricks to improve login time. Search for "improving login time using read ahead" and that should bring some interesting links. In the mean time, I'll check my subscribed threads, I think I have something there...

---

### Post by philinux on 2008-07-30
> **smooth3006 said:**
> i am using both right now but i noticed the graphical interface seems a bit slow when first starting ubuntu. i do have a good graphics card and had envy install the latest drivers.

What are your system specs.

Try running

top

In a terminal and see if anything using high cpu %

---

### Post by overdrank on 2008-07-30
moved :)

---

### Post by smooth3006 on 2008-07-30
> **philinux said:**
> What are your system specs.

Try running

top

In a terminal and see if anything using high cpu %


intel core2duo 6550 2.33ghz.
OCZ Reaper HPC Edition 4GB DDR2 800 (PC2 6400) Dual Channel
nvidia geforce 8800GT 512MB. / thermaltake dual orb vga cooler.
DFI LANPARTY DK P35-T2RS LGA 775 Intel P35 ATX Intel Motherboard.
western digital 250gb & 80gb. 7200 RPM 8MB Cache SATA 3.0Gb/s Hard Drives.
acer 19" x192w widescreen lcd.
raidmax scorpio atx case.
cooler master extreme 500w psu.

---

### Post by smooth3006 on 2008-07-30
> **philinux said:**
> What are your system specs.

Try running

top

In a terminal and see if anything using high cpu %

heres the output :

top - 12:55:57 up 35 min,  2 users,  load average: 0.03, 0.10, 0.09
Tasks: 118 total,   1 running, 117 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.5%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4050220k total,   988540k used,  3061680k free,    20108k buffers
Swap:  5855684k total,        0k used,  5855684k free,   515220k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5544 root      20   0  401m  48m  15m S    1  1.2   1:20.41 Xorg               
 1063 root      15  -5     0    0    0 S    1  0.0   0:00.32 scsi_eh_4          
 7486 smooth    20   0  247m  44m  21m S    1  1.1   0:05.80 compiz.real        
 6049 smooth    20   0  500m 103m  25m S    0  2.6   0:37.28 firefox            
    1 root      20   0  4020  888  600 S    0  0.0   0:00.78 init               
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
   44 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   45 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1

---

### Post by steveneddy on 2008-07-30
compiz is the window manager that makes the cool stuff on your screen and Emerald is the window decoration manager for compiz. 

Compiz must be running for Emerald to run.

You can't run Emerald, the window border decorator without Compiz.

But you can run Compiz without Emerald, just tell it to use Metacity as the window manager/decorator.

---

