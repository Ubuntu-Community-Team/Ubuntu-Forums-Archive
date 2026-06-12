---
title: "Graphic problems with Intel Integrate graphics in 15.10 and 16.04"
date: 2016-05-10
forum: Hardware
---

### Post by gabriel79 on 2016-05-10
Dear Ubuntu Users,

I am struggling with a lots of graphic problems with Kubuntu 16.04 and Kubuntu 15.10 (never had those with 14.04) for my laptop and my girlfriends one.

**Computers characteristics : **
Girlfriend's computer : 
Lenovo U330p
CPU : Intel i5 - 4200U
Screen : 13"
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) 
```

My computer : 
Clevo W540SU
CPU : Intel I7-4702MQ
Screen : 14"
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
```
[B]

List of bugs :[/B]
*Permanent bugs :*
- black screen after returning from sleep mode
- 2 seconds of black screen after login 
- no control of brightness
- When plugging or unplugging a new monitor the new state goes often undetected
- for my computer only, Wrong sized desktop (if I move the cursor to an edge it moves the whole desktop, like it wouldn't fit perfectly)
- Wifi icon not present when unconnected 
*Occasional bug : *
- Black screen after unplugging external monitor, the cursor is stuck in the left edge and goes only up and down

Bugs are override by hard reboot in recovery mode and using dpkg

**Additional information :**
The bugs were there for me since I upgraded to Kubuntu 15.10, the they disappeared when I upgraded to 16.04 and came back after few days of use. When I backed up to a working bakup point the bugs were gone but came back again after few days
For my girlfriend, the bugs weren't there for Kubuntu 15.10 and appeared when I upgraded her laptop to Kubuntu 16.04, we tried to downgrade again but the bugs were still there
[B]
Common features :[/B]
- integrated Intel graphic card
- Dual-Boot windows
- Kubuntu 64bits
- same person performing the installation (me...)

Can somebody help us out ?

---

