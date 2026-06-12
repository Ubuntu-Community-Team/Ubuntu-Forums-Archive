---
title: "macbook pro 13' (2011)"
date: 2015-05-18
forum: Hardware
---

### Post by sypher2 on 2015-05-18
Im currently running Xubuntu (trusty) on my macbook pro. I want to upgrade my RAM from 4GB - 8GB. Is their a way to check my RAM specs via terminal?

---

### Post by Bucky Ball on 2015-05-18
Yep. Open a terminal and:

```
sudo lshw -C memory
```

That should do it, or at least tell you the sort of RAM you need for your machine. If you have the manual, or can get it online, good idea to look at that for the exact specs, e.g. how much RAM the machine can take and the maximum RAM speed that machine can handle. ;)

PS: Here is the bit in the output you should be looking at, from my machine:

```
*-memory
       description: System Memory
       physical id: 18
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
          product: M471B5673FH0-CF8
          physical id: 0
          serial: 9295A0B8
          slot: DIMM0
          size: 2GiB
          width: 64 bits
          clock: 1067MHz (0.9ns)
     *-bank:1
          description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
          product: M471B5673FH0-CF8
          physical id: 1
          serial: 9295A134
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 1067MHz (0.9ns)
```

PPS: Depending on what you're doing with your machine, more RAM may not make any difference whatsoever. If you do a check of how much you are using in your regular routine now (use 'top' in a terminal) you will probably find you are only just tickling the 4Gb. 

If you haven't got one already, though, you WILL notice a difference with an SSD instead of a HDD. That would be where to look for speed improvements. As I say, depends what you do with your machine, of course (if you are doing resource intensive editing of large audio/visual files, more RAM good).

---

### Post by sypher2 on 2015-05-18
> **Bucky Ball said:**
> Yep. Open a terminal and:

```
sudo lshw -C memory
```

That should do it, or at least tell you the sort of RAM you need for your machine. If you have the manual, or can get it online, good idea to look at that for the exact specs, e.g. how much RAM the machine can take and the maximum RAM speed that machine can handle. ;)

PS: Here is the bit in the output you should be looking at, from my machine:

```
*-memory
       description: System Memory
       physical id: 18
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
          product: M471B5673FH0-CF8
          physical id: 0
          serial: 9295A0B8
          slot: DIMM0
          size: 2GiB
          width: 64 bits
          clock: 1067MHz (0.9ns)
     *-bank:1
          description: SODIMM DDR3 Synchronous 1067 MHz (0.9 ns)
          product: M471B5673FH0-CF8
          physical id: 1
          serial: 9295A134
          slot: DIMM1
          size: 2GiB
          width: 64 bits
          clock: 1067MHz (0.9ns)
```

PPS: Depending on what you're doing with your machine, more RAM may not make any difference whatsoever. If you do a check of how much you are using in your regular routine now (use 'top' in a terminal) you will probably find you are only just tickling the 4Gb. 

If you haven't got one already, though, you WILL notice a difference with an SSD instead of a HDD. That would be where to look for speed improvements. As I say, depends what you do with your machine, of course (if you are doing resource intensive editing of large audio/visual files, more RAM good).

THAT WORKED PERFECTLY thank you!!!
does a SSD look like a RAM chip? or does it look entirely different. also, would i have to modify my Mac to hold this SSD? or is their a space for it as well as the RAM slots.

---

### Post by Bucky Ball on 2015-05-18
SSD is a solid state drive. It replaces the hard disk drive (HDD) and is MUCH faster than a regular hard drive. Also more expensive, though. 

What exactly do you do with your machine in your everyday computing? That will help to work out whether you will see any benefit from upgrading the RAM. If you're checking emails, watching Youtube and surfing the net it is doubtful you will see any real discernible difference in speed. 

Glad the RAM commands worked. :)

---

### Post by sypher2 on 2015-05-18
I do alot of school work (many tabs on 2 different monitors), i run photoshop and adobe illustrator on OSX and on xubuntu, i use alot of tools from BackBox and Kali and i use ALOT of terminals running different things for school as well. Its cyber security ITT

---

### Post by Bucky Ball on 2015-05-18
Sounds fairly similar to myself. I have an i3 with 4Gb of RAM, laptop with 24" external monitor attached via HDMI. No issues.

I suggest cranking up everything (go over the top), open a terminal and use 'top' (just type in 'top' and hit enter). Have a look at the stats up the top of that output re. RAM and swap to see if you're RAM is getting bitten and how big that bite is. I would do the same with OSX, particularly with PShop and Illustrator, but can't tell you how to check RAM usage there ...

Find attached my top output. See up the top where it says 'mem'? I have five apps on the go and about 30+ tabs open in Firefox.

---

### Post by sypher2 on 2015-05-18
so i did what you did as well, except i had 4 terminals open running different processes for pen testing as well as 2 browsers open and my RAM sky rocketed as apposed to when i just have 20 browsers open and 5 apps. Its not so much having alot of things open, but having things open that consistently are doing something. I dont know if im making sense.

---

