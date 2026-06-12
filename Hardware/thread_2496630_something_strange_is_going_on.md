---
title: "something strange is going on"
date: 2024-04-05
forum: Hardware
---

### Post by cryofreeze666 on 2024-04-05
i have 2 nvidia cards, and an amd card, in the miner i've built.  haven't tried running it yet, because for some reason the fans on the amd card aren't turning.  i reinstalled windows for sheets and giggles, the card's fans turn there.  is there something wrong with the open source amd drivers that the fans aren't activating (ubuntu 20.04)?  i don't want to burn up the card, it's an rx6800xt, and it cost around 600 bucks when i bought it at the beginning of last year.  do i have to install amd's open source drivers?  is there a setting that needs to be changed?  HW probe says it's there and working, so unless that program isn't that great i'm going to trust it for now.  could someone give me a hand?

operating system ubuntu 20.04
motherboard:  meg x570 unify (ms-7c35
cpu:  not showing on program, i just know its a 12 core ryzen 9
other gpu's:  evga geforce gtx 1050 ti, msi geforce 3060 (lhr) yep, just found out with this program.  annoying they don't put that info on the packaging.

running 64 gig of ram if that info is needed

want to get it up and earning so i can get rid of the 3060, except i don't want to turn it on for long periods right now.  at least till i know whats up with the cards fans, and msi nor amd want to give me much help when i'm using ubuntu.

please don't give me to much greif about the computer, i canabalized it from gamers i don't use any more.

thanks in advance

---

### Post by MAFoElffen on 2024-04-05
Please post the results of this posted within CODE tags:
```

sudo lspci -knnn | grep -A3 -E 'Display|VGA|3D'

```

---

### Post by cryofreeze666 on 2024-04-05
```
ab@ab-MS-7C35:~$ sudo lspci -knnn | grep -A3 -E 'Display|VGA|3D'
 [sudo] password for ab:  
 2a:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:73bf] (rev c3)
     Subsystem: Sapphire Technology Limited Device [1da2:e437]
     Kernel driver in use: amdgpu
     Kernel modules: amdgpu
 --
 2b:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:2504] (rev a1)
     Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:397b]
     Kernel driver in use: nouveau
     Kernel modules: nvidiafb, nouveau
 --
 37:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] [10de:1c82] (rev a1)
     Subsystem: eVga.com. Corp. GP107 [GeForce GTX 1050 Ti] [3842:6253]
     Kernel driver in use: nouveau
     Kernel modules: nvidiafb, nouveau
```

---

### Post by MAFoElffen on 2024-04-07
On Code Tags on an EDIT mode... If you do 
Edit Post > Go Advanced > Highlight the code text you want wrapped > In the extended edit menu, selct the "#" Icon... That will wrap the selected text with CODE Tags.

Once you see what the tags look like, [noparse]```
 Text... 
```[/noparse],you can just enter them in manually

[hr][/hr]
That output shows you are not using nvidia drivers. But rather the opensource nouveau driver...

---

### Post by cryofreeze666 on 2024-04-07
would it make a difference if i installed the linux drivers from amd,  and how would i acyivate them?  will they show up in the  drivers after installed?  also, nvidia cards work fans run, the whole nine yards.  the amd card is the one that the card fans aren't turning while in ubuntu.

---

### Post by QIII on 2024-04-07
Unfortunately, mixing OEMs, and sometimes different cards from the same OEM, is generally impossible in Linux.  A possible exception is a hybrid Intel/AMD or Intel/NVIDIA mix.  But even that requires some effort and it is not often that both can be used at the same time.

Your output indicates that the amdgpu module is active, so nothing to do there.

---

