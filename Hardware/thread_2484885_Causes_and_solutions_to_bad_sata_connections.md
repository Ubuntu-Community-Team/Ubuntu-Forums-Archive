---
title: "Causes and solutions to bad sata connections"
date: 2023-03-13
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2023-03-13
Full dmesg output: [https://pastebin.com/Xx0KBtFF](https://pastebin.com/Xx0KBtFF)

looks like this is usually on ata13, but i have seen it on all of my HDDs
this is my controller
[LIST]
[*][FONT=monospace][COLOR=#000000]2e:00.0 SATA controller: JMicron Technology Corp. JMB58x AHCI SATA controller[/COLOR]
[/FONT]
[*][FONT=monospace][COLOR=#000000]https://www.amazon.com/Internal-Non-Raid-Adapter-Desktop-Support/dp/B07T3RMFFT (got it "refurbished" for ~20 on ebay)[/COLOR][/FONT]
[/LIST]
This is my hot swap bay:
[LIST]
[*][https://www.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/dp/B00DGZ42SM](https://www.amazon.com/Rosewill-5-25-Inch-3-5-Inch-Hot-swap-SATAIII/dp/B00DGZ42SM)
[/LIST]
What i have tried:
[LIST]
[*]cleaning sata connectors with contact cleaner
[*]applying dielectric grease to sata connections (at the controller and inside the hot-swap bays)
[LIST]
[*]i think this has improved the situation, it was worse
[/LIST]

[*]gluing a heatsink to the controller
[/LIST]
Ideas i have:
[LIST]
[*]applying dielectric grease in the back of the sata plugs at the drive cage (hard spot to access)
[*]shielded sata cables (do these exist?)
[LIST]
[*]wrapping the sata cables in aluminum foil and grounding it (as opposed to the above)
[/LIST]

[*]different controller (what else will fit in a M.2 slot?)
[*]maybe it is the hot swap bay?
[/LIST]
Build pics:
[LIST]
[*][https://imgur.com/a/bJsP80E](https://imgur.com/a/bJsP80E)
[/LIST]
note EMI could be the issue, i have a audio amp, modem, boost converter, and a network switch inside the case

I have 4 HDDs in a hot swap cage

Drive config:
```
[FONT=monospace][COLOR=#000000]$ sudo mdadm -D /dev/md2 [/COLOR]
/dev/md2: 
           Version : 1.2 
     Creation Time : Sun Nov 13 14:54:53 2022 
        Raid Level : raid10 
        Array Size : 7813772288 (7.28 TiB 8.00 TB) 
     Used Dev Size : 3906886144 (3.64 TiB 4.00 TB) 
      Raid Devices : 4 
     Total Devices : 4 
       Persistence : Superblock is persistent 

     Intent Bitmap : Internal 

       Update Time : Mon Mar 13 12:21:29 2023 
             State : clean  
    Active Devices : 4 
   Working Devices : 4 
    Failed Devices : 0 
     Spare Devices : 0 

            Layout : near=2 
        Chunk Size : 512K 

Consistency Policy : bitmap 

              Name : niceserver:2  (local to host niceserver) 
              UUID : a1a41d92:421eda05:59f6da66:3d3f0f6e 
            Events : 49779 

    Number   Major   Minor   RaidDevice State 
       0       8      144        0      active sync set-A   /dev/sdj 
       1       8      160        1      active sync set-B   /dev/sdk 
       2       8      128        2      active sync set-A   /dev/sdi 
       3       8      176        3      active sync set-B   /dev/sdl

[/FONT]
```

---

### Post by TheFu on 2023-03-13
JMicron controllers tend to be less-than-great. Sorry.  
I have a few too. All less-than-great, unfortunately.

BTW, running RAID without having partitions is **not** a best practice for a number of reasons.

---

