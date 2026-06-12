---
title: "[SOLVED] GA-MA78GPM-DS2H and  ATI 'Sideport RAM' video"
date: 2008-08-07
forum: Hardware
---

### Post by charonred on 2008-08-07
My Mate has just got himself a Gigabyte [GA-MA78GPM-DS2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2859") mainboard and installed Ubuntu 8.04 - we've done all the updates to 8.04.1 and installed a whole bunch of KDE stuff.

We've enabled the 'restricted' drivers for video and Ubuntu seems to be working fine with the Compiz effects, but KDE has some problems - when trying to log-off, the screen just goes messy (can't see anything but flashing boxes on screen) and so have to power off and reboot. 

He's running a AMD 2.7 Ghz dual-core with 2 GB Corsair DDR2 RAM,
but this new m/board also  has Integrated 128MB DDR3 1066/ 1333(OC)MHz 'SidePort' Memory with Integrated ATI Radeon HD3200 graphics (DirectX10) - we're thinking that as the 'SidePort' video memory is so new that it may be causing some confusion in 'driver land'.

Seeking some advice to fix things

Currently he doesn't have internet or phone line, so he can't go online, hence my post on his behalf - we did all the updates etc by bringing his box over to my place for a few hours to use my internet connection.

---

### Post by phidia on 2008-08-07
What he's experiancing might be a bug-actually conflict with the video driver-in KDE. I'm not sure but if you search > KDE has some problems - when trying to log-off you will find some hits blaming the problem on conflicts with drivers. He could try using xfce (not too hard to install with the package manager) and see if the problem continues or not.

---

### Post by charonred on 2008-08-08
Thanks, 
I phone him later and suggest he tries Xfce and see if the problem continues in that.

If it does or doesn't, what then? 

I'm not that familiar with Linux terminal commands etc, although my mate has played in linux a lot over the past few years and knows a bit about terminal and root user, so he'll make more sense of it than I would.

---

### Post by Xemanth on 2008-08-15
Has he got rid of the problems because I just ordered this mobo also.... ?

I have for it Athlon X2 4850e 2.5 Ghz 45W and 2x 2 Gb A-Data 800 MHz memory kit. Mmm-m :popcorn:

---

### Post by charonred on 2008-08-15
I'll ask him over the weekend and see what he's achieved. 

I'm interested as well cause I'm building another system for another friend using the 'big brother' of that board - [GA-MA78G-DS3H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2800")

This'll basically be an XP 'gaming box' so it may not experience that problem; though I'll do a Wubi install of Ubuntu so he can sample something other than Windoze as well :)

**UPDATE** to above
gave him a phone call and no he didn't resolve it, though he suspects it's as Phidia suggests (a bug/conflict with video driver in KDE).

Anyhow, he's ended up completely 'trashing' the Ubuntu/KDE install - he's now cleaning the disc/partitions up ready for a re-install of Ubuntu, then he'll try adding KDE to the mix and sorting it out again I'll post back if he has the same problem again. He's been playing with various Linux distros for a few years, and is very impressed with Ubuntu, so he's determined to 'nut it out'.

I'm dropping over his place briefly with the first bios release F1 for that board (still hasn't got internet connection)

---

### Post by charonred on 2008-09-09
Ended up returning the board to my supplier; tried the replacement one and it got 2% through Memtest and ERRORs. 

Swapped out the Corsair  2GB DDR2 Twin2X for some Kingston KVR800D2N5K2.2G (2 x 1GB matched), did one complete pass of Memtest without errors, so put the case back together and hooked everything back up - mate is now letting it run for a few hours - see what happens when I drop back later.


Another mate has the GA-MA78G-DS3H and that has been experiencing random power-off/reboot. It has the same spec Kingston memory, but not matched; anyhow, I'll try a memory swap on that later. 

But from other posts on the web, it seems there are others experiencing the same power-off/reboot on *78G* series boards - even though I updated both boards to the latest bios, the problem remains.

A tech mate of mine reckons it may be a yet unresolved bios problem, that's shutting down PC due to 'overheating', even though the systems are are running 30-40 C.

I was about to build another using this board for another friend, but after being told of the random shutting down, I cancelled it and got a GA-MA790X-DS4 instead.

Will post back when I know more on the *78G* series.

---

### Post by charonred on 2008-09-09
GA-MA78GPM-DS2H seems to be working ok now.

When I left my mates place last night; Memtest had been running 4 hours 32 min, and had completed 7 passes without an error - system seems much happier with the Kingston memory.

---

### Post by Xemanth on 2008-09-11
My mobo (GA-MA78GPM-DS2H) arrived couple weeks ago and it works superbly.

I've installed Kubuntu Hardy 64-bit from alternative disc and then upgraded to KDE 4.1. No problems at all. I have fglrx version 8.8.

I can really recommend this board to everybody.

---

### Post by charonred on 2008-09-11
Xemanth
glad it's working for you, it's a nice spec'd board and should do well as a PC or home theatre system. I've yet to check back with my mate on his GA-MA78GPM-DS2H, but assume it's running fine as I've not heard from him :)

as for 
> Another mate has the GA-MA78G-DS3H and that has been experiencing random power-off/reboot

Seems it has a 'overheating problem' - I was over there last night when it shutdown; rebooted and went into bios to check PC Health - CPU was at 51C+ and gradually dropped back to 40C ; system temp had gone over 42C and returned to 36C - rebooted to XP and kept an eye on temp, it gradually crept up (even when doing nothing in XP).

removed and re-installed memory; unclamped CPU heatsink which relieved huge pressure on board (I think the standard AMD heatsink clamp is a faulty one, too much pressure possibly bowing the board), so left clamp hooked onto board's plastic lugs, but not locked down - though I had to pack the lever with a 'match stick' so that there was some pre-load on clamp (otherwise it would be loose, which is not normal).

Also  even on 'optimised defaults' the CPU is running at 1008 Mhz instead of 2700Mhz - 1008Mhz is ok for 'fail safe defaults', but not for optimised; I think there is something wrong here as well - all other AMD 2.7Ghz CPUs that I have installed on systems recently run at 2700Mhz. 

will investigate this further with supplier.

---

### Post by charonred on 2008-09-21
Seems the GA-MA78G-DS3H mainboard was faulty as well.

My supplier replaced and tested it solid for a day with memtest and some game playing; so that PC is now back at my mates place and it's been running fine for the past few days - no probs at all.

The other board GA-MA78GPM-DS2H has been running fine as well for the past week+.

Just bad luck to build 2 PCs with the same new series of boards, and for both to be faulty.

I have another PC to build, so I'm giving the person the option of building with an all included board (GA-MA78G-DS3H), or one that requires a separate graphics card (GA-790X-DS4).

---

### Post by Xemanth on 2008-09-22
> **charonred said:**
> Seems the GA-MA78G-DS3H mainboard was faulty as well.

My supplier replaced and tested it solid for a day with memtest and some game playing; so that PC is now back at my mates place and it's been running fine for the past few days - no probs at all.

The other board GA-MA78GPM-DS2H has been running fine as well for the past week+.

Just bad luck to build 2 PCs with the same new series of boards, and for both to be faulty.

I have another PC to build, so I'm giving the person the option of building with an all included board (GA-MA78G-DS3H), or one that requires a separate graphics card (GA-790X-DS4).

I have had also one faulty mobo but it was abit nforce 4 mobo. It had really weird random poweroffs in linux and windows.

---

