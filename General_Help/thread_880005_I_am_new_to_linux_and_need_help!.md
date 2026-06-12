---
title: "I am new to linux and need help!"
date: 2008-08-04
forum: General Help
---

### Post by ademony on 2008-08-04
I just installed Ubuntu 8.04 and i need help with it.Here is my questions:
1.My configuration is P4 2.4 Ghz/768 MB ram/Nvidia FX5500 graphic card and with this configurations Ubuntu runs very slow. What should i do? Is there any configuration setup?
2.My printer is Xerox Workcentre PE114e and i cannot print anything. It found the driver of PE118e or some printer like that and download it but nothing happens.What should i do? How can i print?
3.For Linux what is the best audio player which can play all lossless formats like APE,FLAC,WAVPACK and these big files with cue sheets?

---

### Post by ibuclaw on 2008-08-04
Slow?

What do you mean when you say slow? Your specs should be more than enough for Ubuntu to function fine.

What does "top" say?
Run
```
top
```
in the terminal and post the output.

Regards
Iain

---

### Post by ademony on 2008-08-04
here is what top says:
top - 22:52:19 up 30 min,  2 users,  load average: 0.10, 0.21, 0.26
Tasks:  98 total,   1 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7%us,  1.3%sy,  0.0%ni, 94.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    775308k total,   540928k used,   234380k free,    15692k buffers
Swap:  1646620k total,        0k used,  1646620k free,   302088k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5060 root      20   0 37904  27m 7856 S  2.0  3.6   0:46.96 Xorg                                                            
 5844 demon     20   0 75644  20m  10m S  0.7  2.7   0:00.56 gnome-terminal                                                  
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.32 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0                                                       
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
  120 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
  154 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  155 root      20   0     0    0    0 S  0.0  0.0   0:00.04 pdflush                                                         
  156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         
  196 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 1459 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 1462 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 1486 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 ata/0                                                           
 1488 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 1722 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 1724 root      15  -5     0    0    0 S  0.0  0.0   0:00.42 scsi_eh_1                                                       
 2405 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kjournald                                                       
 2607 root      16  -4  2520 1040  380 S  0.0  0.1   0:00.44 udevd                                                           
 2962 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                       
 2973 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                      
 4275 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty                                                           
 4276 root      20   0  1716  504  440 S  0.0  0.1   0:00.00 getty                                                           
 4280 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty                                                           
 4281 root      20   0  1716  504  440 S  0.0  0.1   0:00.00 getty                                                           
 4283 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty

---

### Post by tamoneya on 2008-08-04
1. I agree with tinivole
2. not really sure.  I have never messed around that much with printers
3. VLC is my personal favorite.  It is in synaptic/add remove so it will be easy to install.

---

### Post by tamoneya on 2008-08-04
> **ademony said:**
> here is what top says:
top - 22:52:19 up 30 min,  2 users,  load average: 0.10, 0.21, 0.26
Tasks:  98 total,   1 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7%us,  1.3%sy,  0.0%ni, 94.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    775308k total,   540928k used,   234380k free,    15692k buffers
Swap:  1646620k total,        0k used,  1646620k free,   302088k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 5060 root      20   0 37904  27m 7856 S  2.0  3.6   0:46.96 Xorg                                                            
 5844 demon     20   0 75644  20m  10m S  0.7  2.7   0:00.56 gnome-terminal                                                  
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.32 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0                                                       
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
  120 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
  154 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                         
  155 root      20   0     0    0    0 S  0.0  0.0   0:00.04 pdflush                                                         
  156 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                         
  196 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
 1459 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
 1462 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
 1486 root      15  -5     0    0    0 S  0.0  0.0   0:00.24 ata/0                                                           
 1488 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
 1722 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                       
 1724 root      15  -5     0    0    0 S  0.0  0.0   0:00.42 scsi_eh_1                                                       
 2405 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kjournald                                                       
 2607 root      16  -4  2520 1040  380 S  0.0  0.1   0:00.44 udevd                                                           
 2962 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                       
 2973 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                      
 4275 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty                                                           
 4276 root      20   0  1716  504  440 S  0.0  0.1   0:00.00 getty                                                           
 4280 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty                                                           
 4281 root      20   0  1716  504  440 S  0.0  0.1   0:00.00 getty                                                           
 4283 root      20   0  1716  508  440 S  0.0  0.1   0:00.00 getty

That output looks pretty clean.  You are running at 10% CPU load.  How much ram/swap space are you using.  Run this:```
free -m
```

---

### Post by ibuclaw on 2008-08-04
I've looked up the Printer, and it appears to just be a rebranded Samsung SCX4100.

So look up the drivers for that and get it setup with CUPS and hopefully it will work.
[Read here, it seems they got the printer working fine.]("http://ubuntuforums.org/showthread.php?t=597343")

Regards
Iain

---

