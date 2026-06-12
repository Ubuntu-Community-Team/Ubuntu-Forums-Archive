---
title: "Discrete graphic card turned off but still heating"
date: 2013-03-15
forum: Hardware
---

### Post by Tobo27 on 2013-03-15
Hi all!

I'm having some trouble with this Laptop: HP pavilion g6 1364sl  
 
Intel i5 2450M 
ATI radeon 6400(6450 maybe)M 
Intel HD 3000 
Ram 4GB 
 
Running ubuntu 12.04 up to date.

Well, I finally succeded in turning off ati video card (or at least that's what ubuntu says):

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```

and:

```
lspci -vnnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] [1002:6760] (rev ff) (prog-if ff)
```

According to the instructions I found on the net, this should mean that discrete card is turned off.

If i check GPU temperature with sensors
```
radeon-pci-0100
Adapter: PCI adapter
temp1:       -128.0°C  

```

Which makes me suppose that the discrete card is really turned off.

Here's the matter: I can still feel heat coming from the laptop area that was overheating with ati turned on. I thought that it was due to thermal inertia, but after a night turned off, it's heating again. Not as much as before (ati on), but still hotter than Windows 8!

Do you have some suggest? anyone have had this issue before and knows how to fix it?

thanks in advance! :)
Tobo.

---

