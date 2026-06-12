---
title: "Overheating problem with Ubuntu OS"
date: 2018-12-18
forum: Hardware
---

### Post by andrea.mamprin on 2018-12-18
Hi there.
I've installed Ubuntu OS 18.04 on my desktop PC and I'm experimenting overheating all the time. Very basic tasks (like launching Chrome for example) rises core's temperature at 70º C-80º C, a video stream boost it over 90 degrees, and the fans are continuously working. 
This problem was also present with Ubuntu 16.04, but under windows 10 everything was fine. I've read a lot of posts about ubuntu overheating issues, I've tried some solutions (installing thermald, tlp, etc.) with no results.
[COLOR=#141414]Can anyone help me? Thanks in advance.[/COLOR]

OS: Ubuntu 18.04.1 LTS
Processor: Intel® Core™ i5-3330 CPU @ 3.00GHz × 4
Graphics: Intel® Ivybridge Desktop
Gnome: 3.28.2
OS type: 64-bit

---

### Post by QIII on 2018-12-18
Hello!

Who is the OEM and what is the model number of your machine?

---

### Post by andrea.mamprin on 2018-12-18
> **QIII said:**
> Hello!

Who is the OEM and what is the model number of your machine?

Thank you for your very prompt response.

My pc is an assembled one. The motherboard is Asus P8H61-M LX3 R2.0. 
Is this information useful for you?

---

### Post by QIII on 2018-12-18
There may be something about that particular motherboard and Linux somewhere.  I'll look as I have time.

In the meantime, let's check to see if you have a runaway process or something.

When it gets hot, please issue the following in the command line:

```
top
```

Paste back the results.

---

### Post by QIII on 2018-12-18
All I am finding is to use thermald or tlp, which you have already tried.

How did you configure them?

---

### Post by andrea.mamprin on 2018-12-18
> **QIII said:**
> There may be something about that particular motherboard and Linux somewhere.  I'll look as I have time.

In the meantime, let's check to see if you have a runaway process or something.

When it gets hot, please issue the following in the command line:

```
top
```

Paste back the results.


Here it is!

```

top - 23:42:00 up 7 min,  1 user,  load average: 10,60, 4,19, 1,76
Tasks: 287 total,   2 running, 234 sleeping,   0 stopped,   1 zombie
%Cpu(s): 58,4 us, 32,3 sy,  0,0 ni,  3,4 id,  5,3 wa,  0,0 hi,  0,6 si,  0,0 st
KiB Mem :  7860000 total,  2701372 free,  2863912 used,  2294716 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  4263428 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                        
 2828 andrea    20   0 1052080 348316  77620 R  68,4  4,4   0:11.98 chrome                                                                                                                                         
 2665 andrea    20   0 1106680 248048  99020 S  39,9  3,2   0:17.10 chrome                                                                                                                                         
 2848 andrea    20   0  996520 343092  77372 S  38,5  4,4   0:09.84 chrome                                                                                                                                         
 2913 root     -51   0       0      0      0 S  34,2  0,0   0:02.42 kidle_inject/0                                                                                                                                 
 2914 root     -51   0       0      0      0 S  34,2  0,0   0:02.42 kidle_inject/1                                                                                                                                 
 2915 root     -51   0       0      0      0 S  34,2  0,0   0:02.42 kidle_inject/2                                                                                                                                 
 2916 root     -51   0       0      0      0 S  34,2  0,0   0:02.42 kidle_inject/3                                                                                                                                 
 1861 andrea    20   0 3353328 241724  59720 S  23,6  3,1   1:58.22 dropbox                                                                                                                                        
 2222 andrea    20   0 1799760 241964 120624 S  19,3  3,1   0:11.73 chrome                                                                                                                                         
 2527 andrea    20   0  849552 169912  65780 S  18,6  2,2   0:10.68 chrome                                                                                                                                         
 2288 andrea    20   0  599420 129532  91340 S  12,6  1,6   0:06.09 chrome                                                                                                                                         
 1617 andrea    20   0 3850244 327264  73064 S  10,3  4,2   0:23.39 gnome-shell                                                                                                                                    
 2732 andrea    20   0 1072504 123676  70384 S   5,3  1,6   0:01.21 chrome                                                                                                                                         
 1487 andrea    20   0  373448  79892  56880 S   4,7  1,0   0:03.88 Xorg                                                                                                                                           
 1638 andrea     9 -11 1696656  12924   9672 S   1,3  0,2   0:00.69 pulseaudio                                                                                                                                     
 2253 andrea    20   0  800524  37660  27680 S   1,3  0,5   0:00.49 gnome-terminal-                                                                                                                                
 2566 andrea    20   0  748924  99140  70596 S   1,0  1,3   0:00.38 chrome                                                                                                                                         
 2814 andrea    20   0  822804 152212  77208 S   1,0  1,9   0:02.11 chrome                                                                                                                                         
 1053 gdm       20   0 3308568 119352  65140 S   0,7  1,5   0:02.10 gnome-shell                                                                                                                                    
 2359 andrea    20   0   51484   4216   3480 R   0,7  0,1   0:00.19 top                                                                                                                                            
   17 root      20   0       0      0      0 I   0,3  0,0   0:00.20 kworker/1:0                                                                                                                                    
   47 root      20   0       0      0      0 I   0,3  0,0   0:00.17 kworker/2:1                                                                                                                                    
  198 root       0 -20       0      0      0 I   0,3  0,0   0:00.33 kworker/2:1H                                                                                                                                   
  227 root      20   0       0      0      0 D   0,3  0,0   0:00.19 jbd2/sda2-8                                                                                                                                    
 2200 andrea    20   0  813292  39172  30456 S   0,3  0,5   0:01.12 psensor                                                                                                                                        
 2474 andrea    20   0  720188  84152  60836 S   0,3  1,1   0:00.26 chrome                                                                                                                                         
 2776 andrea    20   0  733500  92676  63856 S   0,3  1,2   0:00.38 chrome                                                                                                                                         
    1 root      20   0  225444   9176   6604 S   0,0  0,1   0:01.24 systemd                                                                                                                                        
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd                                                                                                                                       
    4 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 kworker/0:0H                                                                                                                                   
    5 root      20   0       0      0      0 I   0,0  0,0   0:00.05 kworker/u8:0                                                                                                                                   
    6 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 mm_percpu_wq                                                                                                                                   
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.01 ksoftirqd/0                                                                                                                                    
    8 root      20   0       0      0      0 I   0,0  0,0   0:00.22 rcu_sched                                                                                                                                      
    9 root      20   0       0      0      0 I   0,0  0,0   0:00.00 rcu_bh                                                                                                                                         
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/0                                                                                                                                    
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/0                                                                                                                                     
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0                                                                                                                                        
   13 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/1                                                                                                                                        
   14 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/1                                                                                                                                     
   15 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 migration/1                                                                                                                                    
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.01 ksoftirqd/1                                                                                                                                    
   18 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 kworker/1:0H                                                                                                                                   
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/2                                                                                                                                        
   20 root      rt   0       0      0      0 S   0,0  0,0   0:00.00 watchdog/2
```

---

### Post by andrea.mamprin on 2018-12-18
> **QIII said:**
> All I am finding is to use thermald or tlp, which you have already tried.

How did you configure them?

I only installed them, the instructions I've found are not explaining about configuration.
However, I've tried to configure intel_pstate with no results.

---

### Post by QIII on 2018-12-18
There appear to be two problems:

1.  Chrome is sucking up a lot of cycles on at least one of your cores.

2.  kidle_inject is sucking up a lot.

For the kidle_inject issue, you might want to look through [this confirmed-but-not-resolved bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389077") on launchpad.  It's four years old, but there may be a regression.

---

### Post by QIII on 2018-12-18
By the way, please enclose all commands and output from the terminal in code tags.  That preserves formatting and makes your posts easier to read.

To use code tags, either:

1.  Click the "paperclip" icon in the toolbar, place your cursor between the code tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the paperclip button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following your text.  The square brackets are required.

---

### Post by Doug S on 2018-12-19
I would suggest using turbostat (linux-tools-common package) to attempt to assess what is going on with your computer. For just an overview:
```
sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15
```And then perhaps more to see that it is actually going into deep idle states when the inject stuff is used (not sure what your deepest idle state is):
```
sudo turbostat --quiet --Summary --hide Avg_MHz,SMI,GFXMHz,TSC_MHz,GFXWatt,CorWatt,CPU%c1,CPU%c3,CPU%c6,CPU%c7,CoreTmp,G*&#8203;FX%rc6,Pkg%pc2,Pkg%pc3,Pkg%pc6 --interval 15
```
check your idle states with:
```
grep . /sys/devices/system/cpu/cpu0/cpuidle/state*/name
```
You could try disabling intel_powerclamp, and use thermald instead, using [this config file]("https://askubuntu.com/questions/897217/cpu-overheating-on-ubuntu-16-04-msi-ge40/897856#897856").

EDIT: By the way, that motherboard should not have a cooling problem. i.e. you should be able to go flat out without exceeding critical temperatures. Are your fans working O.K. and your thermal paste between your processor and heat sink good?

---

### Post by andrea.mamprin on 2018-12-19
> **QIII said:**
> There appear to be two problems:

1.  Chrome is sucking up a lot of cycles on at least one of your cores.

2.  kidle_inject is sucking up a lot.

For the kidle_inject issue, you might want to look through [this confirmed-but-not-resolved bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1389077") on launchpad.  It's four years old, but there may be a regression.


Thanks for the suggestion.
My feeling is that the overheating is not depending on a specific process.
I'm starting monitoring the top processes in different moments when temperature boosts.
In the case shown below, for example, the temperature rises when I start downloading podcasts with Rhythmbox and backup them with Dropbox.

```
andrea@andreaUbu:~$ top

top - 13:07:41 up  1:33,  1 user,  load average: 2,68, 2,73, 1,97
Tasks: 308 total,   2 running, 252 sleeping,   0 stopped,   1 zombie
%Cpu(s): 12,2 us,  0,8 sy,  0,0 ni, 63,5 id, 23,2 wa,  0,0 hi,  0,3 si,  0,0 st
KiB Mem :  7860000 total,  1291672 free,  3054204 used,  3514124 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  4096596 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1879 andrea    20   0 3406560 615588  64828 S  37,9  7,8  13:08.16 dropbox     
 1630 andrea    20   0 3869492 338188  76348 S   5,3  4,3   3:50.40 gnome-shell 
 7955 andrea    20   0  545624  20732  12048 R   4,0  0,3   0:29.09 gvfsd-http  
 1500 andrea    20   0  407184  86048  60148 S   2,0  1,1   1:02.98 Xorg        
 8968 andrea    20   0 1452868  82972  44860 S   1,3  1,1   0:15.75 rhythmbox   
10247 andrea    20   0  799180  36472  27572 S   0,7  0,5   0:00.32 gnome-term+ 
  208 root       0 -20       0      0      0 I   0,3  0,0   0:02.66 kworker/2:+ 
  239 root      20   0       0      0      0 D   0,3  0,0   0:04.29 jbd2/sda2-8 
 1613 andrea    20   0  220772   6932   6216 S   0,3  0,1   0:00.51 at-spi2-re+ 
 1840 andrea    20   0 1265568  74444  43940 S   0,3  0,9   0:08.82 nautilus-d+ 
 1865 andrea    20   0  204888   6680   6020 S   0,3  0,1   0:00.92 ibus-engin+ 
 2135 andrea    20   0  813288  38808  30100 S   0,3  0,5   0:21.03 psensor     
 3741 andrea    20   0 3210436 305604 119732 S   0,3  3,9   0:33.51 chrome      
 4209 andrea    20   0 1546100  97180  65956 S   0,3  1,2   0:05.04 chrome      
 4896 andrea    20   0 1598020 122484  75520 S   0,3  1,6   0:03.71 chrome      
 6006 root      20   0       0      0      0 I   0,3  0,0   0:01.26 kworker/u8+ 
 6075 andrea    20   0 1337400 250172 129068 S   0,3  3,2   1:49.78 chrome      

```

There is no trace of kidle_inject.

However I attemp to manage the priority of temperature controllers editing the file thermal-cpu-cdev-order.xml, as described in the link you suggest, but with no results.

---

### Post by andrea.mamprin on 2018-12-19
> **Doug S said:**
> I would suggest using turbostat (linux-tools-common package) to attempt to assess what is going on with your computer. For just an overview:
```
sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15
```And then perhaps more to see that it is actually going into deep idle states when the inject stuff is used (not sure what your deepest idle state is):
```
sudo turbostat --quiet --Summary --hide Avg_MHz,SMI,GFXMHz,TSC_MHz,GFXWatt,CorWatt,CPU%c1,CPU%c3,CPU%c6,CPU%c7,CoreTmp,G*&#8203;FX%rc6,Pkg%pc2,Pkg%pc3,Pkg%pc6 --interval 15
```
check your idle states with:
```
grep . /sys/devices/system/cpu/cpu0/cpuidle/state*/name
```
You could try disabling intel_powerclamp, and use thermald instead, using [this config file]("https://askubuntu.com/questions/897217/cpu-overheating-on-ubuntu-16-04-msi-ge40/897856#897856").

EDIT: By the way, that motherboard should not have a cooling problem. i.e. you should be able to go flat out without exceeding critical temperatures. Are your fans working O.K. and your thermal paste between your processor and heat sink good?

Hi Doug. Thank you for your contribution.
The turbostat analysis give the following data.

```
andrea@andreaUbu:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15[sudo] password for andrea: 
Busy%    Bzy_MHz    PkgTmp    PkgWatt
4.38    2603    63    25.75
1.51    2031    63    23.51
2.85    2475    62    24.59
1.22    1818    61    24.01
1.63    1953    60    23.51
1.28    1724    59    23.17
3.46    2394    61    24.52
2.70    2344    59    25.20
10.04    2567    67    29.59
12.39    2643    65    29.70
13.86    2643    67    30.95
14.33    2662    76    31.00
22.43    2934    78    35.67
21.12    2779    78    37.99
17.50    2697    77    36.34
25.22    2818    85    40.96
24.42    2784    86    40.79
17.77    2761    83    36.73
14.17    2574    79    33.47

```


my idle states
```
andrea@andreaUbu:~$ grep . /sys/devices/system/cpu/cpu0/cpuidle/state*/name/sys/devices/system/cpu/cpu0/cpuidle/state0/name:POLL
/sys/devices/system/cpu/cpu0/cpuidle/state1/name:C1
/sys/devices/system/cpu/cpu0/cpuidle/state2/name:C1E
/sys/devices/system/cpu/cpu0/cpuidle/state3/name:C3
/sys/devices/system/cpu/cpu0/cpuidle/state4/name:C6

```

```
andrea@andreaUbu:~$ sudo turbostat --quiet --Summary --hide Avg_MHz,SMI,GFXMHz,TSC_MHz,GFXWatt,Corwatt,CPU%c1,CPU%c3,CPU%c6,CoreTmp,G*&#8203;FX%rc6,Pkg%pc2,Pkg%pc3,Pkg%pc6 --interval 15
Busy%    Bzy_MHz    IRQ    C1    C1E    C3    C6    C1%    C1E%    C3%    C6%    CPU%c7    PkgTmp    GFX%rc6    PkgWatt    CorWatt
10.99    2232    16991    4741    6185    3439    28857    2.29    7.21    2.76    76.17    0.00    86    0.00    34.89    8.07
13.75    2378    21575    4588    7775    4568    29719    2.92    7.25    3.26    72.13    0.00    80    0.93    37.34    9.69
11.12    2223    16548    3137    5505    3341    22681    3.16    5.03    2.50    77.76    0.00    78    16.11    34.11    8.11
2.97    2328    5929    1593    698    166    5444    6.06    0.73    0.21    89.99    0.00    69    7.19    24.94    4.47
3.58    2440    5613    1996    1031    324    5533    7.11    1.40    0.29    87.55    0.00    70    8.00    24.93    4.62
19.40    2606    36846    5971    9158    5907    26624    2.90    6.06    4.27    66.64    0.00    77    10.16    36.26    10.65
27.58    2822    42141    7888    13483    6430    19703    4.23    6.81    3.74    56.89    0.00    89    11.20    40.69    14.21
12.84    2409    30271    4401    9994    6862    23248    4.06    5.31    3.90    73.34    0.00    82    17.52    33.94    8.96
15.72    2286    28128    3782    10391    5523    38875    2.40    8.83    4.39    67.66    0.00    83    0.00    38.59    10.52
12.48    1973    24399    2820    7578    4006    39524    1.44    7.73    3.24    74.19    0.00    89    0.00    36.78    8.71
18.77    2473    25589    2857    7607    3753    37100    1.71    7.45    3.02    68.06    0.00    84    0.00    40.20    11.60

```

My fans are o.k., just cleaned the pc a few months ago. I don't known was is the state of thermal paste, but I'll investigate with my assistant.

---

### Post by Doug S on 2018-12-19
Your processor is getting hotter than expected for what it is doing. It is properly going into deep idle states which consume negligible power. I am a server guy, so I always forget about graphics. Have a look with this command (from memory, I might not have syntax or position of "GFXWatt" correct):

```
sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,GFXWatt,PkgTmp,PkgWatt --interval 15
```
Could you also post the big spew of stuff at the start of the command if you delete the "--quiet" option.

---

### Post by andrea.mamprin on 2018-12-19
> **Doug S said:**
> Your processor is getting hotter than expected for what it is doing. It is properly going into deep idle states which consume negligible power. I am a server guy, so I always forget about graphics. Have a look with this command (from memory, I might not have syntax or position of "GFXWatt" correct):

```
sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,GFXWatt,PkgTmp,PkgWatt --interval 15
```
Could you also post the big spew of stuff at the start of the command if you delete the "--quiet" option.

Here it is:

```
andrea@andreaUbu:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,GFXWatt,PkgTmp,PkgWatt --interval 15[sudo] password for andrea: 
Busy%    Bzy_MHz    PkgTmp    PkgWatt    GFXWatt
5.57    2606    64    24.71    0.79
7.97    2668    64    25.92    1.23
8.13    2594    65    27.90    2.45
3.11    2375    62    23.56    0.29
18.70    2998    79    31.94    2.58
11.26    2842    77    27.82    0.79
14.49    2869    69    33.03    3.63
7.93    2632    71    29.45    3.46
10.44    2567    69    30.43    3.41
2.93    1968    65    24.82    1.26
10.91    2557    70    30.48    3.52
15.19    2589    76    35.08    5.68
4.36    2083    72    29.31    3.96
3.50    2104    69    27.14    2.97
30.09    2794    93    41.27    6.45
21.63    2515    77    35.04    4.07
17.99    2262    74    30.43    2.47
15.62    2082    72    28.70    2.12
31.11    2603    85    41.24    6.36
32.80    2623    90    47.33    9.49
27.88    2329    93    44.69    9.81
26.51    2245    92    44.60    10.17
29.45    2414    96    47.70    11.01
22.79    2146    89    41.87    9.40

```


```
turbostat version 17.06.23 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:3a:9 (6:58:9)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM TM
CPUID(6): APERF, TURBO, DTS, PTM, No-HWP, No-HWPnotify, No-HWPwindow, No-HWPepp, No-HWPpkg, EPB
cpu1: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST No-MWAIT PREFETCH TURBO)
CPUID(7): No-SGX
cpu1: MSR_MISC_PWR_MGMT: 0x00400000 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 851 sec. Joule Counter Range, at 77 Watts
cpu1: MSR_PLATFORM_INFO: 0x81010e0011e00
16 * 100.0 = 1600.0 MHz max efficiency frequency
30 * 100.0 = 3000.0 MHz base frequency
cpu1: MSR_IA32_POWER_CTL: 0x0014005d (C1E auto-promotion: DISabled)
cpu1: MSR_TURBO_RATIO_LIMIT: 0x1e1f2020
30 * 100.0 = 3000.0 MHz max turbo 4 active cores
31 * 100.0 = 3100.0 MHz max turbo 3 active cores
32 * 100.0 = 3200.0 MHz max turbo 2 active cores
32 * 100.0 = 3200.0 MHz max turbo 1 active cores
cpu1: MSR_CONFIG_TDP_NOMINAL: 0x0000001e (base_ratio=30)
cpu1: MSR_CONFIG_TDP_LEVEL_1: 0x1e0000000000000 (PKG_MIN_PWR_LVL1=480 PKG_MAX_PWR_LVL1=0 LVL1_RATIO=0 PKG_TDP_LVL1=0)
cpu1: MSR_CONFIG_TDP_LEVEL_2: 0x1e0000000000000 (PKG_MIN_PWR_LVL2=480 PKG_MAX_PWR_LVL2=0 LVL2_RATIO=0 PKG_TDP_LVL2=0)
cpu1: MSR_CONFIG_TDP_CONTROL: 0x80000000 ( lock=1)
cpu1: MSR_TURBO_ACTIVATION_RATIO: 0x00000000 (MAX_NON_TURBO_RATIO=0 lock=0)
cpu1: MSR_PKG_CST_CONFIG_CONTROL: 0x1e008402 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=2: pc6n)
cpu1: cpufreq driver: acpi-cpufreq
cpu1: cpufreq governor: ondemand
cpufreq boost: 1
cpu1: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000000 (performance)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0xd000001e00268 (77 W TDP, RAPL 60 - 0 W, 0.012695 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x8000830200148268 (locked)
cpu0: PKG Limit #1: ENabled (77.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: ENabled (96.250000 Watts, 0.000977* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00691400 (105 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x881d0002 (76 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (105 C, 105 C)
cpu1: MSR_PKGC3_IRTL: 0x0000883b (valid, 60416 ns)
cpu1: MSR_PKGC6_IRTL: 0x00008850 (valid, 81920 ns)
cpu1: MSR_PKGC7_IRTL: 0x00008857 (valid, 89088 ns)

```

---

### Post by Doug S on 2018-12-19
As I mentioned previously, your processor seems to run too hot for the given load. I assume you have a good processor heat sink with an attached fan. (?) Is the fan spinning faster when the processor is hot? If it were me, I would toss out anything else attempting to throttle things, and use thermald with the configuration file I pointed to earlier, but set to 75 or 80 degrees.

---

### Post by andrea.mamprin on 2018-12-19
Yes, my fans are cooling faster, that was the clue that made me realize that there was a high temperatures issue.
My PSU is Thermaltake toughpower gold 750w.

Now, I'll try to configure thermald as you suggest and I'll tell you what happens.

---

### Post by andrea.mamprin on 2018-12-19
I've changed the [COLOR=#24292E][FONT=-apple-system]thermal-conf.xml[/FONT][/COLOR] file changing <Temperature> from 55000 to 75000. Is it right? Well... it seems to me that nothing relevant happens with processor temperature.

---

### Post by Doug S on 2018-12-19
> **andrea.mamprin said:**
> I've changed the [COLOR=#24292E][FONT=-apple-system]thermal-conf.xml[/FONT][/COLOR] file changing <Temperature> from 55000 to 75000. Is it right? Well... it seems to me that nothing relevant happens with processor temperature.Just for a test, change it to 45 degrees. Does that have an effect? Is thermald running? What command do you use to re-start it with the new configuration file?

My test server is doing a 17 hour test at the moment, so i can not try it just now.

---

### Post by andrea.mamprin on 2018-12-19
> **Doug S said:**
> Just for a test, change it to 45 degrees. Does that have an effect? Is thermald running? What command do you use to re-start it with the new configuration file?

My test server is doing a 17 hour test at the moment, so i can not try it just now.

When I changed the thermal-conf.xml parameter, I execute in terminal the following code

```
sudo service thermald restart
```

Is it right? How can I understand if thermld is running?

---

### Post by CatKiller on 2018-12-20
It does sound like a thermal interface problem to me. The fans are going crazy because they're cooling the heatsink, which isn't in thermal contact with the cpu, and the cpu isn't getting any cooler.

Even with a crappy heatsink, under heavy load, your processor wouldn't be getting that hot if the interface were good.

---

### Post by QIII on 2018-12-20
Is this a dual-boot system.  Does it still behave normally in Windows if it is?

Have you recently opened the machine and perhaps bumped the cooler?

---

### Post by Doug S on 2018-12-20
You can observe the status of thermald via:

```
doug@s15:~/idle$ [COLOR="#FF0000"]sudo systemctl status thermald.service[/COLOR]
[sudo] password for doug:
&#9679; thermald.service - Thermal Daemon Service
   Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2018-12-19 23:50:55 PST; 2min 52s ago
 Main PID: 13755 (thermald)
    Tasks: 2
   Memory: 1.5M
      CPU: 23ms
   CGroup: /system.slice/thermald.service
           &#9492;&#9472;13755 /usr/sbin/thermald --no-daemon --dbus-enable

Dec 19 23:50:55 s15 systemd[1]: Starting Thermal Daemon Service...
Dec 19 23:50:55 s15 systemd[1]: Started Thermal Daemon Service.
Dec 19 23:50:55 s15 thermald[13755]: 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
Dec 19 23:50:55 s15 thermald[13755]: Polling mode is enabled: 4
Dec 19 23:50:55 s15 thermald[13755]: XML zone: invalid sensor type []

```You can re-start it via:
```
sudo systemctl restart thermald.service
```
I re-installed it on my test server and set the trigger temperature to 55 degrees. I fully loaded all of my CPUs with thermald disabled, then enabled it. Turbostat output:
```
doug@s15:~$ [COLOR="#FF0000"]sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15[/COLOR]
Busy%   Bzy_MHz PkgTmp  PkgWatt
100.00  3400    66      57.75
100.00  3400    67      58.23
100.00  3400    69      58.59
100.00  3400    70      58.85
100.00  3400    71      58.97
100.00  3199    65      54.54  <<< Thermald service started.
98.96   1678    58      23.68
71.25   1600    55      17.26
69.45   1600    54      16.82
88.33   1600    54      20.33
100.00  1600    52      22.44
100.00  1909    54      27.60
100.00  2114    55      31.15
100.00  1743    56      24.72
100.00  1862    51      26.85
100.00  2045    56      29.91
100.00  2035    53      29.79
100.00  1869    55      26.99
100.00  1945    53      28.20
100.00  1909    54      27.62
100.00  1770    55      25.23
100.00  1817    54      26.08

```EDIT: I am using the intel_pstate CPU frequency scaling driver and the powersave governor. For less extreme temperature control thermald limits CPU via the max percent setting:
```
doug@s15:~/idle$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
60
```If the temperature is still too high, even at minimum CPU frequency, then thermald starts to use "kidle_inject", which is why you see my "Busy%" drop below 100%, for a short time, above. Also:
```
doug@s15:~$ sudo turbostat --quiet --Summary --hide Avg_MHz,SMI,GFXMHz,TSC_MHz,GFXWatt,CorWatt,IRQ,POLL,C1,C1E,C3,C6,CPU%c1,CPU%c3,CPU%c6,CPU%c7,CoreTmp,GFX%rc6,Pkg%pc2,Pkg%pc3,Pkg%pc6 --interval 5
Busy%   Bzy_MHz POLL%   C1%     C1E%    C3%     C6%     PkgTmp  PkgWatt
100.00  3400    0.00    0.00    0.00    0.00    0.00    74      59.69
100.00  3400    0.00    0.00    0.00    0.00    0.00    74      59.74
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.69
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.69
100.00  3400    0.00    0.00    0.00    0.00    0.00    74      59.68
100.00  3400    0.00    0.00    0.00    0.00    0.00    76      59.74
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.72
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.74
100.00  3241    0.00    0.00    0.00    0.00    0.00    71      56.11   <<< Thermald enabled
100.00  2358    0.00    0.00    0.00    0.00    0.00    65      36.86   <<< Thermald starts by lowering the maximum CPU frequency
100.00  1712    0.00    0.00    0.00    0.00    0.00    62      24.71
99.88   1600    0.00    0.00    0.00    0.00    0.12    61      22.77    <<<< Processor is still too hot, even at minimum CPU frequency. Thermald starts using kidle_inject
92.67   1600    0.00    0.00    0.00    0.00    7.34    60      21.36    <<<< Kidle_inject forces C6, the deepest and lowest energy idle state (for mine, and your, processor)
80.66   1600    0.00    0.00    0.00    0.00    19.35   58      19.07
61.64   1600    0.00    0.00    0.00    0.00    38.38   56      15.49
50.57   1600    0.00    0.00    0.00    0.00    49.45   56      13.51
49.85   1600    0.00    0.00    0.00    0.00    50.17   55      13.35  <<<< Minimum CPU frequency and 50% idle.
49.85   1600    0.00    0.00    0.00    0.00    50.17   55      13.33
49.85   1600    0.00    0.00    0.00    0.00    50.17   53      13.28
49.85   1600    0.00    0.00    0.00    0.00    50.18   52      13.28
49.85   1600    0.00    0.00    0.00    0.00    50.18   52      13.23
51.60   1600    0.00    0.00    0.00    0.00    48.42   51      13.56  <<<< Temperature undershoots target
57.74   1600    0.00    0.00    0.00    0.00    42.28   51      14.71
64.30   1600    0.00    0.00    0.00    0.00    35.71   51      15.86
71.26   1600    0.00    0.00    0.00    0.00    28.75   51      17.17
77.15   1600    0.00    0.00    0.00    0.00    22.86   52      18.18
83.29   1600    0.00    0.00    0.00    0.00    16.72   51      19.30
89.44   1600    0.00    0.00    0.00    0.00    10.57   52      20.44
96.26   1600    0.00    0.00    0.00    0.00    3.74    52      21.70
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.38  <<<< Thermald has now removed kidle_inject
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.41
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.38
100.00  1668    0.00    0.00    0.00    0.00    0.00    53      23.42  <<<< And even starts to increase the CPU max Frequency
100.00  2071    0.00    0.00    0.00    0.00    0.00    56      30.24
100.00  2050    0.00    0.00    0.00    0.00    0.00    53      29.98
100.00  2220    0.00    0.00    0.00    0.00    0.00    55      33.10
100.00  1832    0.00    0.00    0.00    0.00    0.00    53      26.17
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.40
100.00  1788    0.00    0.00    0.00    0.00    0.00    55      25.44  <<<< It is not a great servo system, so oscillates some.
100.00  1660    0.00    0.00    0.00    0.00    0.00    54      23.42
100.00  1991    0.00    0.00    0.00    0.00    0.00    55      28.85
100.00  2129    0.00    0.00    0.00    0.00    0.00    55      31.47
100.00  1712    0.00    0.00    0.00    0.00    0.00    53      24.26
100.00  1609    0.00    0.00    0.00    0.00    0.00    53      22.63

```

I noticed you are using the acpi-cpufreq CPU scaling driver. I do not know how thermald works with it, but I assume it does.

---

### Post by andrea.mamprin on 2018-12-20
> **QIII said:**
> Is this a dual-boot system.  Does it still behave normally in Windows if it is?

Have you recently opened the machine and perhaps bumped the cooler?

No my system is not a dual-boot one. Only ubtuntu. A few months ago I was using windows OS and the fans was very noiseless. Then I install ubuntu 16.04 and the fan start work harder. I supposed the problem was due to an excessive use of processor, a batch R script that download json file via Twitter Rest Api is running all the time. I discover that R was creating a giant history archive that blocked my memory. Once this problem has been overcome, the fan was reducing their work just a little bit. Some weeks ago I upgraded Ubuntu (18.04) and for a few days I've not worked with the batch script. Neverthless the fan was cooling almost all the time. So i keep exploring the overheating problem.

I'm not an expert in the hardware part, so this work is done by a computer technician. It was cleaning the pc a few months ago, when ubuntu was already installed. It seems to me that the fan action was the same before and after cleaning.

---

### Post by CatKiller on 2018-12-20
The thermal paste goes between the processor and the heatsink. I'm sure the fans are keeping the heatsink nice and cool, but not actually cooling the processor itself.

Air is a rubbish thermal conductor, so you use paste to keep contact between the chip and heatsink without any bubbles.

---

### Post by andrea.mamprin on 2018-12-21
> **Doug S said:**
> You can observe the status of thermald via:

```
doug@s15:~/idle$ [COLOR=#FF0000]sudo systemctl status thermald.service[/COLOR]
[sudo] password for doug:
&#9679; thermald.service - Thermal Daemon Service
   Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2018-12-19 23:50:55 PST; 2min 52s ago
 Main PID: 13755 (thermald)
    Tasks: 2
   Memory: 1.5M
      CPU: 23ms
   CGroup: /system.slice/thermald.service
           &#9492;&#9472;13755 /usr/sbin/thermald --no-daemon --dbus-enable

Dec 19 23:50:55 s15 systemd[1]: Starting Thermal Daemon Service...
Dec 19 23:50:55 s15 systemd[1]: Started Thermal Daemon Service.
Dec 19 23:50:55 s15 thermald[13755]: 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
Dec 19 23:50:55 s15 thermald[13755]: Polling mode is enabled: 4
Dec 19 23:50:55 s15 thermald[13755]: XML zone: invalid sensor type []

```You can re-start it via:
```
sudo systemctl restart thermald.service
```
I re-installed it on my test server and set the trigger temperature to 55 degrees. I fully loaded all of my CPUs with thermald disabled, then enabled it. Turbostat output:
```
doug@s15:~$ [COLOR=#FF0000]sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15[/COLOR]
Busy%   Bzy_MHz PkgTmp  PkgWatt
100.00  3400    66      57.75
100.00  3400    67      58.23
100.00  3400    69      58.59
100.00  3400    70      58.85
100.00  3400    71      58.97
100.00  3199    65      54.54  <<< Thermald service started.
98.96   1678    58      23.68
71.25   1600    55      17.26
69.45   1600    54      16.82
88.33   1600    54      20.33
100.00  1600    52      22.44
100.00  1909    54      27.60
100.00  2114    55      31.15
100.00  1743    56      24.72
100.00  1862    51      26.85
100.00  2045    56      29.91
100.00  2035    53      29.79
100.00  1869    55      26.99
100.00  1945    53      28.20
100.00  1909    54      27.62
100.00  1770    55      25.23
100.00  1817    54      26.08

```EDIT: I am using the intel_pstate CPU frequency scaling driver and the powersave governor. For less extreme temperature control thermald limits CPU via the max percent setting:
```
doug@s15:~/idle$ cat /sys/devices/system/cpu/intel_pstate/max_perf_pct
60
```If the temperature is still too high, even at minimum CPU frequency, then thermald starts to use "kidle_inject", which is why you see my "Busy%" drop below 100%, for a short time, above. Also:
```
doug@s15:~$ sudo turbostat --quiet --Summary --hide Avg_MHz,SMI,GFXMHz,TSC_MHz,GFXWatt,CorWatt,IRQ,POLL,C1,C1E,C3,C6,CPU%c1,CPU%c3,CPU%c6,CPU%c7,CoreTmp,GFX%rc6,Pkg%pc2,Pkg%pc3,Pkg%pc6 --interval 5
Busy%   Bzy_MHz POLL%   C1%     C1E%    C3%     C6%     PkgTmp  PkgWatt
100.00  3400    0.00    0.00    0.00    0.00    0.00    74      59.69
100.00  3400    0.00    0.00    0.00    0.00    0.00    74      59.74
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.69
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.69
100.00  3400    0.00    0.00    0.00    0.00    0.00    74      59.68
100.00  3400    0.00    0.00    0.00    0.00    0.00    76      59.74
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.72
100.00  3400    0.00    0.00    0.00    0.00    0.00    75      59.74
100.00  3241    0.00    0.00    0.00    0.00    0.00    71      56.11   <<< Thermald enabled
100.00  2358    0.00    0.00    0.00    0.00    0.00    65      36.86   <<< Thermald starts by lowering the maximum CPU frequency
100.00  1712    0.00    0.00    0.00    0.00    0.00    62      24.71
99.88   1600    0.00    0.00    0.00    0.00    0.12    61      22.77    <<<< Processor is still too hot, even at minimum CPU frequency. Thermald starts using kidle_inject
92.67   1600    0.00    0.00    0.00    0.00    7.34    60      21.36    <<<< Kidle_inject forces C6, the deepest and lowest energy idle state (for mine, and your, processor)
80.66   1600    0.00    0.00    0.00    0.00    19.35   58      19.07
61.64   1600    0.00    0.00    0.00    0.00    38.38   56      15.49
50.57   1600    0.00    0.00    0.00    0.00    49.45   56      13.51
49.85   1600    0.00    0.00    0.00    0.00    50.17   55      13.35  <<<< Minimum CPU frequency and 50% idle.
49.85   1600    0.00    0.00    0.00    0.00    50.17   55      13.33
49.85   1600    0.00    0.00    0.00    0.00    50.17   53      13.28
49.85   1600    0.00    0.00    0.00    0.00    50.18   52      13.28
49.85   1600    0.00    0.00    0.00    0.00    50.18   52      13.23
51.60   1600    0.00    0.00    0.00    0.00    48.42   51      13.56  <<<< Temperature undershoots target
57.74   1600    0.00    0.00    0.00    0.00    42.28   51      14.71
64.30   1600    0.00    0.00    0.00    0.00    35.71   51      15.86
71.26   1600    0.00    0.00    0.00    0.00    28.75   51      17.17
77.15   1600    0.00    0.00    0.00    0.00    22.86   52      18.18
83.29   1600    0.00    0.00    0.00    0.00    16.72   51      19.30
89.44   1600    0.00    0.00    0.00    0.00    10.57   52      20.44
96.26   1600    0.00    0.00    0.00    0.00    3.74    52      21.70
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.38  <<<< Thermald has now removed kidle_inject
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.41
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.38
100.00  1668    0.00    0.00    0.00    0.00    0.00    53      23.42  <<<< And even starts to increase the CPU max Frequency
100.00  2071    0.00    0.00    0.00    0.00    0.00    56      30.24
100.00  2050    0.00    0.00    0.00    0.00    0.00    53      29.98
100.00  2220    0.00    0.00    0.00    0.00    0.00    55      33.10
100.00  1832    0.00    0.00    0.00    0.00    0.00    53      26.17
100.00  1600    0.00    0.00    0.00    0.00    0.00    52      22.40
100.00  1788    0.00    0.00    0.00    0.00    0.00    55      25.44  <<<< It is not a great servo system, so oscillates some.
100.00  1660    0.00    0.00    0.00    0.00    0.00    54      23.42
100.00  1991    0.00    0.00    0.00    0.00    0.00    55      28.85
100.00  2129    0.00    0.00    0.00    0.00    0.00    55      31.47
100.00  1712    0.00    0.00    0.00    0.00    0.00    53      24.26
100.00  1609    0.00    0.00    0.00    0.00    0.00    53      22.63

```

I noticed you are using the acpi-cpufreq CPU scaling driver. I do not know how thermald works with it, but I assume it does.


Following your suggestion I've checked if termald was working. The status is active, nevertheless the ouput tells me that "sysfs write failed".

> andrea@andreaUbu:~$ sudo systemctl status thermald.service[sudo] password for andrea: 
&#9679; thermald.service - Thermal Daemon Service
   Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset:
   Active: active (running) since Fri 2018-12-21 09:49:43 -05; 1h 36min ago
 Main PID: 814 (thermald)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/thermald.service
           &#9492;&#9472;814 /usr/sbin/thermald --no-daemon --dbus-enable


dic 21 09:49:44 andreaUbu thermald[814]: 13 CPUID levels; family:model:stepping 
dic 21 09:49:44 andreaUbu thermald[814]: Polling mode is enabled: 4
dic 21 09:49:42 andreaUbu systemd[1]: Starting Thermal Daemon Service...
dic 21 09:49:43 andreaUbu systemd[1]: Started Thermal Daemon Service.
dic 21 09:49:46 andreaUbu thermald[814]: sysfs write failed /sys/devices/virtual
dic 21 11:06:36 andreaUbu thermald[814]: sysfs write failed /sys/devices/virtual
dic 21 11:06:36 andreaUbu thermald[814]: sysfs write failed /sys/devices/virtual
lines 1-15/15 (END)...skipping...
&#9679; thermald.service - Thermal Daemon Service
   Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2018-12-21 09:49:43 -05; 1h 36min ago
 Main PID: 814 (thermald)
    Tasks: 2 (limit: 4915)
   CGroup: /system.slice/thermald.service
           &#9492;&#9472;814 /usr/sbin/thermald --no-daemon --dbus-enable


dic 21 09:49:44 andreaUbu thermald[814]: 13 CPUID levels; family:model:stepping 0x6:3a:9 (6:58:9)
dic 21 09:49:44 andreaUbu thermald[814]: Polling mode is enabled: 4
dic 21 09:49:42 andreaUbu systemd[1]: Starting Thermal Daemon Service...
dic 21 09:49:43 andreaUbu systemd[1]: Started Thermal Daemon Service.
dic 21 09:49:46 andreaUbu thermald[814]: sysfs write failed /sys/devices/virtual/powercap/intel-rapl/intel-rapl:0/enabled
dic 21 11:06:36 andreaUbu thermald[814]: sysfs write failed /sys/devices/virtual/powercap/intel-rapl/intel-rapl:0/enabled
dic 21 11:06:36 andreaUbu thermald[814]: sysfs write failed /sys/devices/virtual/powercap/intel-rapl/intel-rapl:0/constraint_0_power_limit_uw




In this [link]("https://github.com/intel/thermal_daemon/issues/148#issuecomment-388573608") I found this tip: "This probably means that the system vendor has disabled modifying the power limits for the CPU". Is it right? How can I bypass this situation?

---

### Post by CatKiller on 2018-12-21
Have you got ```
intel_pstate=enable
``` in your grub? It used to be a necessary step, but I don't know if it still is.

---

### Post by andrea.mamprin on 2018-12-21
> **CatKiller said:**
> Have you got ```
intel_pstate=enable
``` in your grub? It used to be a necessary step, but I don't know if it still is.

Yes I've enabled it and then disabled it. It seems to me that the fan works harder when pstate is enabled.

---

### Post by Doug S on 2018-12-21
> **andrea.mamprin said:**
> In this [link]("https://github.com/intel/thermal_daemon/issues/148#issuecomment-388573608") I found this tip: "This probably means that the system vendor has disabled modifying the power limits for the CPU". Is it right? How can I bypass this situation?For my configuration file, you don't need to bypass the situation, because it shouldn't exist. That stuff is disabled for my processor also. (use the intel_pstate CPU frequency scaling driver)

---

### Post by Doug S on 2018-12-21
> **CatKiller said:**
> Have you got ```
intel_pstate=enable
``` in your grub? It used to be a necessary step, but I don't know if it still is.It is no longer needed. It is the default CPU frequency driver for the appropriate Intel processors.

---

### Post by pqwoerituytrueiwoq on 2018-12-21
Unless your ambient temp is near unbearable you should not be able to get temps of 80C+ without a synthetic stress test (or mining software) running without a hardware level issue, bad cooler mount, bad paste application, no airflow
you should make sure the cooler is mounted properly and you have a good paste application
A lot of people flip out about how paste is applied, but given you use a NON-CONDUCTIVE paste, too little paste means overheating, too much makes cleaning it off in the future a mess
*Some CPU coolers come with a peal off plastic cover on the bottom you need to remove before installing
can you take some pictures around the cpu cooler in your system, maybe it is bad enough for us to see something from them


If you see lower temps with another OS this is probably why
The GPU load heating up the cpu, gnome is probably keeping the gpu under enough load it can not idle
if this is correct you will see lower temps using xubuntu or lubuntu, you can test this live

Assuming this is just cause the load is very high cause of the gnome desktop eating the GPU's processing power you could get a older gaming class GPU like the GTX 600 series or RX 400 series or getting a better cpu cooler like a Hyper 212 which run 15 to 30 USD make sure it will fit in your case before buying

---

