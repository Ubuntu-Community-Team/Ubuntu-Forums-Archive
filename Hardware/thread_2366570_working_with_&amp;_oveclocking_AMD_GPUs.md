---
title: "working with &amp; oveclocking AMD GPUs"
date: 2017-07-19
forum: Hardware
---

### Post by akos.maroy on 2017-07-19
Hi,

I started working with AMD GPUs on an ubuntu server for computational purposes. I'm trying to figure out how to make them work efficiently and also how to overclock them. I have had good results with nVidia cards in this respect, but my results with AMD are not that good. I'll compare results with nVidia here and then, where nVidia experiences are with the same motherboard.

I've tried ubuntu 17.04 and also 16.04 LTS. the results are similar. the specific examples below come from 16.04 LTS, as it is said that AMD supports LTS only.

Any pointers below appreciated.

I have an [ASRock H81 Pro BTC 2.0]("http://www.asrock.com/mb/Intel/H81%20Pro%20BTC%20R2.0/") motherboard with 6 ASUS AMD RX 580 cards connected. All cards show up as expected. I also see them through the /sys/class/drm/cardX/device interface:

```
$ cat /sys/class/drm/card[1-6]/device/pp_num_states
states: 2
0 boot
1 performance
states: 2
0 boot
1 performance
states: 2
0 boot
1 performance
states: 2
0 boot
1 performance
states: 2
0 boot
1 performance
states: 2
0 boot
1 performance
$ cat /sys/class/drm/card[1-6]/device/pp_cur_state
1
1
1
1
1
1
$ cat /sys/class/drm/card[1-6]/device/pp_dpm_pcie
0: 2.5GB, x8 *
1: 5.0GB, x16 
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
$ cat /sys/class/drm/card[1-6]/device/pp_dpm_sclk
0: 300Mhz 
1: 600Mhz 
2: 900Mhz 
3: 1162Mhz 
4: 1233Mhz 
5: 1275Mhz 
6: 1319Mhz 
7: 1360Mhz 
0: 300Mhz 
1: 600Mhz 
2: 900Mhz 
3: 1162Mhz 
4: 1233Mhz 
5: 1275Mhz 
6: 1319Mhz 
7: 1360Mhz *
0: 300Mhz 
1: 600Mhz *
2: 900Mhz 
3: 1162Mhz 
4: 1233Mhz 
5: 1275Mhz 
6: 1319Mhz 
7: 1360Mhz 
0: 300Mhz 
1: 600Mhz *
2: 900Mhz 
3: 1162Mhz 
4: 1233Mhz 
5: 1275Mhz 
6: 1319Mhz 
7: 1360Mhz 
0: 300Mhz 
1: 600Mhz 
2: 900Mhz 
3: 1162Mhz 
4: 1233Mhz 
5: 1275Mhz 
6: 1319Mhz 
7: 1360Mhz *
0: 300Mhz 
1: 600Mhz *
2: 900Mhz 
3: 1162Mhz 
4: 1233Mhz 
5: 1275Mhz 
6: 1319Mhz 
7: 1360Mhz 
$ cat /sys/class/drm/card[1-6]/device/pp_dpm_mclk
0: 300Mhz 
1: 1000Mhz 
2: 1750Mhz 
0: 300Mhz 
1: 1000Mhz 
2: 1750Mhz *
0: 300Mhz *
1: 1000Mhz 
2: 1750Mhz 
0: 300Mhz *
1: 1000Mhz 
2: 1750Mhz 
0: 300Mhz 
1: 1000Mhz 
2: 1750Mhz *
0: 300Mhz *
1: 1000Mhz 
2: 1750Mhz 

```

the above are displayed when the cards are under computational load.

as you see, the cards are not really putting out peak performance. also, the cards behave differently, although the load on them is the same.

most notably:

1. card1 is on an x8 PCI connection, while all others are on x16:

```
$ cat /sys/class/drm/card[1-6]/device/pp_dpm_pcie
0: 2.5GB, x8 *
1: 5.0GB, x16 
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *
0: 2.5GB, x8 
1: 5.0GB, x16 *

```

and I don't see the way to change this. as a result, card1 operates significantly (about 4 times) slower. on the same motherboard, there are no such issues with nVidia. I don't see any option to set this bus speed in the BIOS. it's also strange that the x16 option is there, but it's still x8 for card1, while x16 for all others. (one can't just "echo 1 > pp_dpm_pcie", it's not a read-write interface)


2. memory and GPU clock speeds are inconsistent

see above for the pp_dpm_sclk and pp_dpm_mclk outputs. again, card1 behaves strangely in the sense that no * (indication) appears beside the memory clock readings. also, while all cards are under computational load, some have a 300MHz memory clock, while others 1750MHz. I'd prefer to set this to 1750MHz, for all of them.


3. I've tried to use ROC-smi from AMD: [https://github.com/RadeonOpenCompute/ROC-smi](https://github.com/RadeonOpenCompute/ROC-smi) , but it's not really giving good results. 

```

$ ./rocm-smi 

====================    ROCm System Management Interface    ====================
================================================================================
 GPU  DID    Temp     AvgPwr   SCLK     MCLK     Fan      Perf    OverDrive  ECC
GPU[0] 		: PowerPlay not enabled - Cannot get supported clocks
GPU[0] 		: PowerPlay not enabled - Cannot get supported clocks
  0   0402   N/A      N/A      N/A      N/A      None%              N/A      N/A      
  1   67df   48.0c    N/A      N/A      N/A      42.75%   auto      0%       N/A      
  2   67df   74.0c    N/A      600Mhz   1750Mhz  85.88%   auto      0%       N/A      
  3   67df   76.0c    N/A      300Mhz   1000Mhz  84.71%   auto      0%       N/A      
  4   67df   72.0c    N/A      600Mhz   1750Mhz  83.92%   auto      0%       N/A      
  5   67df   66.0c    N/A      600Mhz   1750Mhz  82.75%   auto      0%       N/A      
  6   67df   61.0c    N/A      600Mhz   300Mhz   84.71%   auto      0%       N/A      
================================================================================
====================           End of ROCm SMI Log          ====================

```

note: card0 is the built-in motherboard card

note that it can't read card1 GPU and clock speeds either.

moreover, if I try ti set anything, the cards will somehow reconfigure and reduce their computing capacity. basically using ROC-smi will somehow put the cards into some minimal configuration state. totally not what one would expect.

I also tried amdcovc: [https://github.com/matszpk/amdcovc](https://github.com/matszpk/amdcovc)  - with similarly bad results.

needless to say, nvidia-smi works with nVidia cards on the same motherboard fine (with the caveat that it needs an X server running on each card)


can any one point me into directions I can make these cards work? get card1 to work on an x16 bus? set memory clocks explicitly?

as you see, it's not even at the point of overclocking at first, at first I just want to get these cards to work properly.

---

