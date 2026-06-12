---
title: "Hissing CPU"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by SKK on 2008-01-04
Since the upgrade to Gutsy I've been hearing some sort of hissing sound from within the computer chassi - but only when using Ubuntu! If I boot into Windows there's no hissing at all!

Unlike ["Odd Hissing When CPU Idle"](http://ubuntuforums.org/showthread.php?t=60139) *my* hissing isn't coming from any speakers or such -  I've managed to determine that the sound is coming from (or near) the CPU and the sound often, but not always, disappears when the CPU is not idle! At first I thought that perhaps it was the CPU fan but it checked out OK!

Considering that the hissing only occurs in Ubuntu it has got to be an Ubuntu issue, right..? Do anyone have any ideas or thoughts about what's causing this? It's beginning to be extremly annoying and, for all I know, potentially damaging to my computer.

Hard-/software info...

Motherboard: Gigabyte GA-M57SLI-S4
CPU: AMD Athlon64 X2 Dual-Core 5600+
CPU Fan: Scythe Katana 2
RAM: Corsair XMS2-6400
GFX Card: Gigabyte GeForce 7600GS SilentPipe
HDD: 2 x Samsung HD501LJ (SATA)
OS: Ubuntu 7.10 and Windows XP Pro

TIA, Stefan

---

### Post by ukripper on 2008-01-04
it could be your fan running on full speed rather than getting scaled with cpu usage. first check BIOS forCPU FAN setting what temperature it is suppose to kick in for full speed.

Then we troubleshoot further.

---

### Post by SKK on 2008-01-04
> **ukripper said:**
> it could be your fan running on full speed rather than getting scaled with cpu usage. first check BIOS forCPU FAN setting what temperature it is suppose to kick in for full speed.

Then we troubleshoot further.

Noo... I'm currently running the computer with an open chassi to monitor the sound and as far as I can tell there's no change in fan speed whether I'm checking the BIOS, running Windows or running Ubuntu. But anyway...

CPU Temp:  ~30°C
CPU Fan Speed: ~840 RPM
CPU Warning Temp: 60°C/140°F

---

### Post by ukripper on 2008-01-04
Can you post output of the folwoing command when it makes hissing sound:

```
top
```

---

### Post by SKK on 2008-01-04
Here you are...

```

top - 14:16:44 up 26 min,  2 users,  load average: 0.20, 0.15, 0.18
Tasks: 168 total,   1 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.4%us,  1.5%sy,  0.0%ni, 90.0%id,  2.6%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   3116304k total,   931176k used,  2185128k free,    26032k buffers
Swap:  1076344k total,        0k used,  1076344k free,   522620k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                                                                 
 7155 root      15   0  165m  37m 9328 S   60  1.2   0:58.62 Xorg                                                                                                                                                                                                                    
 7993 stekar    16   0  177m  77m  22m S    4  2.5   0:59.14 firefox-bin                                                                                                                                                                                                             
    1 root      15   0  2952 1856  532 S    0  0.1   0:01.14 init                                                                                                                                                                                                                    
    2 root      16  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                                                                
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                                                                                                             
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                                                                                                                                             
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                                                                              
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                                                                                                             
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                                                                                                                                             
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                                                                              
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                                                                                                                                
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                                                                                                                                                
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                                                                 
   31 root      12  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                                                                                                                               
   32 root      13  -5     0    0    0 S    0  0.0   0:00.01 kblockd/1                                                                                                                                                                                                               
   33 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                                                                                                  
   34 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                                                                                            
  170 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                                                                                                                 
  197 root      21   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                                                                                 
  198 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                                                                                 
  199 root      16  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                                                                                                                                 
  250 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                                                                                                   
  251 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                                                                                                   
 2037 root      16  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                                                                                           
 2038 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                                                                                                   
 2091 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                                                                                                                                                   
 2092 root      10  -5     0    0    0 S    0  0.0   0:00.28 ata/1                                                                                                                                                                                                                   
 2093 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                                                                                                 
 2173 root      10  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                                                                                                                                
 2247 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                                                                                                                               
 2248 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                                                                                                               
 2292 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                                                                                                                               
 2293 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                                                                                                                               
 2320 root      10  -5     0    0    0 S    0  0.0   0:00.06 scsi_eh_4                                                                                                                                                                                                               
 2321 root      10  -5     0    0    0 S    0  0.0   0:00.04 scsi_eh_5                                                                                                                                                                                                               
 2786 root      10  -5     0    0    0 S    0  0.0   0:00.04 kjournald                                                                                                                                                                                                               
 2881 root      10  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                                                                                                                                             
 2882 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_7                                                                                                                                                                                                               
 2883 root      13  -5     0    0    0 S    0  0.0   0:00.00 usb-storage                                                                                                                                                                                                             
 2996 root      13  -4  3048 1400  408 S    0  0.0   0:00.24 udevd                                                                                                                                                                                                                   
 4162 root      16  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                                                                                                                                               
 4960 root      10  -5     0    0    0 S    0  0.0   0:00.00 kjournald                                                                                                                                                                                                               
 4961 root      11  -5     0    0    0 S    0  0.0   0:00.00 kjournald                                                                                                                                                                                                               
 4962 root      10  -5     0    0    0 S    0  0.0   0:00.06 kjournald                                                                                                                                                                                                               
 4969 root      10  -5     0    0    0 S    0  0.0   0:00.00 reiserfs/0                                                                                                                                                                                                              
 4970 root      10  -5     0    0    0 S    0  0.0   0:00.00 reiserfs/1                                                                                                                                                                                                              
 4979 root      15   0  4988  932  544 S    0  0.0   0:00.00 mount.ntfs-3g                                                                                                                                                                                                           
 5083 root      15   0  4988  932  544 S    0  0.0   0:00.00 mount.ntfs-3g                                                                                                                                                                                                           
 5224 daemon    15   0  1816  512  412 S    0  0.0   0:00.00 portmap                                                                                                                                                                                                                 
 5243 statd     17   0  1876  720  616 S    0  0.0   0:00.00 rpc.statd                                                                                                                                                                                                               
 5351 root      18   0  1696  520  448 S    0  0.0   0:00.00 getty                                                                                                                                                                                                                   
 5352 root      18   0  1696  516  448 S    0  0.0   0:00.00 getty                                                                                                                                                                                                                   
 5354 root      18   0  1696  520  448 S    0  0.0   0:00.00 getty                                                                                                                                                                                                                   
 5357 root      18   0  1692  512  448 S    0  0.0   0:00.00 getty                                                                                                                                                                                                                   
 5358 root      18   0  1696  516  448 S    0  0.0   0:00.00 getty                                                                                                                                                                                                                   
 5359 root      18   0  1692  516  448 S    0  0.0   0:00.00 getty                                                                                                                                                                                                                   
 5547 root      15   0  2432 1320  676 S    0  0.0   0:00.00 acpid                                                                                                                                                                                                                   
 5587 root      10  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0                                                                                                                                                                                                             
 5588 root      20  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1                                                                                                                                                                                                             
 5660 syslog    18   0  2040  812  644 S    0  0.0   0:00.06 syslogd                                                                                                                                                                                                                 
 5716 root      15   0  1840  540  444 S    0  0.0   0:00.04 dd                                                                                                                                                                                                                      
 5718 klog      18   0  2512 1396  408 S    0  0.0   0:00.04 klogd                                                                                                                                                                                                                   
 5739 messageb  15   0  3032 1200  768 S    0  0.0   0:00.40 dbus-daemon                                                                                                                                                                                                             
 5755 root      17   0 13584 2064 1772 S    0  0.1   0:00.02 NetworkManager                                                                                                                                                                                                          
 5768 root      15   0  3276 1280 1116 S    0  0.0   0:00.01 NetworkManagerD

```

I've just been listening with a "stethoscope" (rolled up paper :)) to try and figure out *exactly* where the sound is coming from - sadly I can't point to an exact spot and due to the layout of the MB I'm beginning to think that the GFX card is a possible suspect also. :/

---

### Post by ukripper on 2008-01-04
i wonder why your Xorg using 60% of your CPU

---

### Post by money2themax on 2008-01-04
Tasks: 168 total,   1 running, 167 sleeping,   0 stopped,   0 zombie

whats a zombie

---

### Post by SKK on 2008-01-04
Good question! And I'm beginning to think it IS the GFX card that's hissing! The GPU temp is about 15°C higher than it usually is! The thermal monitor in nvidia-settings is actually showing yellow! :(

Well... I'm going to exchange the GFX card and check the settings on x.org - hopefully that will stop the noise, but if it doesn't I guess I'll be back!

Thanks for the help! :)

Stefan

---

### Post by SKK on 2008-01-04
No! it wasn't the GFX card! But at least the CPU usage of Xorg is down to between 1-2 % with a peaks up to 8% now and then! Regarding the temperature I'm beginning to regret buying a fanless GFX card! :(

So does anyone have any ideas? A new "top" gives...

```

top - 19:13:49 up 7 min,  2 users,  load average: 0.04, 0.33, 0.23
Tasks: 159 total,   1 running, 158 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us,  0.7%sy,  0.0%ni, 97.3%id,  0.0%wa,  0.0%hi,  0.8%si,  0.0%st
Mem:   3116304k total,   660460k used,  2455844k free,    18456k buffers
Swap:  1076344k total,        0k used,  1076344k free,   320452k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                            
 6999 root      15   0 68420  30m 8992 S    1  1.0   0:13.93 Xorg                                                                                                                                                                               
 7680 stekar    15   0 10392 4120 3272 S    1  0.1   0:04.49 conky                                                                                                                                                                              
 7731 stekar    15   0  223m  81m  23m S    0  2.7   0:26.93 firefox-bin                                                                                                                                                                        
 7738 stekar    15   0 41500  16m  10m S    0  0.5   0:00.89 gnome-terminal                                                                                                                                                                     
 7764 stekar    15   0  2496 1196  876 R    0  0.0   0:01.10 top                                                                                                                                                                                
    1 root      19   0  2952 1852  532 S    0  0.1   0:01.14 init                                                                                                                                                                               
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                                                                        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                                                                                                        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                                         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                                                                        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                                                                                                        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                                         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                                                                                           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/1                                                                                                                                                                           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                            
   31 root      12  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                                                                                          
   32 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                                                                                          
   33 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                                                             
   34 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                                                       
  170 root      10  -5     0    0    0 S    0  0.0   0:00.01 kseriod                                                                                                                                                                            
  197 root      21   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                                            
  198 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                                            
  199 root      16  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                                                                                            
  250 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                                                              
  251 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                                                              
 2034 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                                                      
 2035 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                                                              
 2115 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                                                                                                              
 2117 root      10  -5     0    0    0 S    0  0.0   0:00.02 ata/1                                                                                                                                                                              
 2119 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                                                            
 2192 root      10  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                                                                                           
 2285 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                                                                                          
 2286 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                                                                          
 2332 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                                                                                          
 2333 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                                                                                          
 2388 root      10  -5     0    0    0 S    0  0.0   0:00.02 scsi_eh_4                                                                                                                                                                          
 2389 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                                                                                                          
 2408 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                                                                                                                                          
 2409 root      10  -5     0    0    0 S    0  0.0   0:00.00 usb-storage                                                                                                                                                                        
 2717 root      10  -5     0    0    0 S    0  0.0   0:00.01 kjournald                                                                                                                                                                          
 2777 root      10  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                                                                                                        
 2925 root      12  -4  3048 1400  408 S    0  0.0   0:00.17 udevd

```

---

### Post by band-aid on 2008-01-04
this is a complete stab in the dark but have you tried remounting your Heatsink/Fan on your CPU. It may not be seated properly and might be causing some kind of strange thermal activity.

---

### Post by woodcarver on 2008-01-04
Band-aid is right, remount the fan to the CPU, is there thermo-grease or a thermo-wafer between them? If not you need it!
As for your GFX card with no fan, you can buy small fans that will work, or a heat-synk. If you go with the heat-synk, add an extra fan blowing in at the card.

---

### Post by steveneddy on 2008-01-04
> **band-aid said:**
> this is a complete stab in the dark but have you tried remounting your Heatsink/Fan on your CPU. It may not be seated properly and might be causing some kind of strange thermal activity.

This was the direction I was thinking of.

I have had a few PC's make strange sounds in the past. My new laptop made odd noises when it was about 3-4 months old, but at this time it is pretty quiet at almost a year.

My desktop/server at home with a PIII makes odd hissing noises sometimes and I just attribute it to the  MB getting hot and stretching, maybe with the little plastic feet that are mounted between the MB and case causing a little heat related vibration.

Weird but PC's can get create some odd sounds, as do TV's, DVD players and other electronic equipment.

:popcorn:

---

### Post by SKK on 2008-01-04
Yep! Remounted the heatsink twice, with the fan both sucking and blowing, and put on fresh silverbased grease both times!

As for the GFX card it has a heatsink but I'm definately going to add a fan!!! I just played STALKER for about an hour and checked the temperature right after... 93°Celsius!!!!! I turned the front fan around and now both the front and the back fans are "sucking" air from the ventilation hole on the side of the chassi (right above the GFX card) and the temperature at least now stays under 50°Celsius. :/

But like I said - the odd thing is that the computer only makes those hissing noises when I'm using Ubuntu!

---

### Post by ukripper on 2008-01-05
Then i suspect it could be hdd spinning fast under ubuntu. Try accessing ubuntu from external hard disk or usb or try live cd first.

---

### Post by money2themax on 2008-01-05
> **SKK said:**
> Yep! Remounted the heatsink twice, with the fan both sucking and blowing, and put on fresh silverbased grease both times!

As for the GFX card it has a heatsink but I'm definately going to add a fan!!! I just played STALKER for about an hour and checked the temperature right after... 93°Celsius!!!!! I turned the front fan around and now both the front and the back fans are "sucking" air from the ventilation hole on the side of the chassi (right above the GFX card) and the temperature at least now stays under 50°Celsius. :/

But like I said - the odd thing is that the computer only makes those hissing noises when I'm using Ubuntu!
can you record the sound? and post a MP3 of that sound?

---

### Post by steveneddy on 2008-01-05
> **money2themax said:**
> can you record the sound? and post a MP3 of that sound?

cool...

---

### Post by SKK on 2008-01-05
> **ukripper said:**
> Then i suspect it could be hdd spinning fast under ubuntu. Try accessing ubuntu from external hard disk or usb or try live cd first.

Nope! No such luck! Today I've tested with the desktop CD, with "nv" instead of "nvidia" in xorg.conf just for the hell of it, swapped GFX card, hooked them up SLI-style and finally rearranged my whole desk so I would be able to listen better to determine from where and from which part the noise is coming! And that final point is the most frustrating one... I can't for the life of me make out which part it is!!! For all I know it could be the CPU or the GPU, the RAM or even the motherboard itself! :mad:

I have however been able to determine what it's not! It's NOT the HDD! It's NOT the CPU fan (or any other fan for that matter)! It's NOT the PSU!

I'm currently thinking about buying another GFX card just to rule that out! :(

---

### Post by SKK on 2008-01-05
> **money2themax said:**
> can you record the sound? and post a MP3 of that sound?

I'll try!

---

### Post by money2themax on 2008-01-05
> **SKK said:**
> I'll try!
some times it's better t let other hear too cuz we are all just guessing with out hearing theres only so much we can do

---

### Post by SKK on 2008-01-05
OK! Minor "success"! It's the exact problem as in the link I posted in my first post!

When I plugged in the microphone the sound all of a sudden came from the speakers! In other words the illusive sound is coming from the PC speaker. :/

So... Do anyone have any ideas or thoughts about *this* then! :)

And a big thanks to everyone for the suggestions sofar! At least now I won't have to buy a new GFX card! :D

---

### Post by SKK on 2008-01-05
Tried everything in [this thread](http://ubuntuforums.org/showthread.php?t=328288) without success...

---

### Post by money2themax on 2008-01-05
> **SKK said:**
> OK! Minor "success"! It's the exact problem as in the link I posted in my first post!

When I plugged in the microphone the sound all of a sudden came from the speakers! In other words the illusive sound is coming from the PC speaker. :/

So... Do anyone have any ideas or thoughts about *this* then! :)

And a big thanks to everyone for the suggestions sofar! At least now I won't have to buy a new GFX card! :D

so wait you speakers are the problem!?! umm...you didn't unplug them before hunting for the sound?

i'd say it's the soundcard's fault

---

### Post by SKK on 2008-01-05
> **money2themax said:**
> so wait you speakers are the problem!?! umm...you didn't unplug them before hunting for the sound?

i'd say it's the soundcard's fault

Well it appears to be the motherboards onboard PC-speaker that's the source of the hissing/static. The "real" speakers didn't pick up the sound until I plugged in the mic and as soon as I pulled it out they stopped again! 

And like I said before - it only makes this noise when I'm using Ubuntu so I don't think the soundcard is to blame. Otherwise it ought to be heard when I boot into Windows, wouldn't it..?

---

### Post by money2themax on 2008-01-05
try another set of drivers for the sound card

---

### Post by SKK on 2008-01-05
> **money2themax said:**
> try another set of drivers for the sound card

How do I do that? I'm no beginner with Linux/Ubuntu but sound has so far always "just worked"!

---

### Post by money2themax on 2008-01-05
Applications > Other > Sound System
go to the hardware tab and the first drop down menu should explain everything

---

### Post by SKK on 2008-01-06
Nope! Tested just about every combination I could think of, but it made no difference at all.

---

### Post by ukripper on 2008-01-06
try putting headphones straight to soundcard and test whether it is soundcard or speakers.

---

### Post by money2themax on 2008-01-06
well i hope you figure it out i'll try to help the best i can

---

### Post by SKK on 2008-01-06
> **ukripper said:**
> try putting headphones straight to soundcard and test whether it is soundcard or speakers.

No static in the headphones so I suppose it's a soundcard/sound driver issue then! I'm going to check if the same thing happens with Feisty and if not I guess I'll either downgrade or just put up with it and wait for Hardy to be released. :(

I'm thinking about testing the script that jpoe tried [in the thread I linked to in my first post](http://ubuntuforums.org/showthread.php?t=60139), but can anyone explain what it really does?

---

### Post by SKK on 2008-01-06
OK! It's settled! It's a hardware issue! The same hissing can now be heard when I'm running Windows too and it's getting louder and louder. It seems that Ubuntu is just a bit more sensitive (for better or worse) and picked it up first.

I'll have to take it up with the retailer, but thanks again to everyone who tried to help! :)

---

