---
title: "fakeraid 3112 a7n8x deluxe"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by mnnence on 2007-03-22
Hello all. I have officially given up trying to install Ubuntu on a fakeraid a7n8x deluxe asus mobo. I had 2 harddrives striped sata and tried everything I could find. It seems that chipset is just a problem? I backed out of my stripe and installed ubuntu on 1 hdd and xp on the other. I am not happy. It is significantly slower in xp ( and I assume ubuntu ). I tried edgy dapper feisty in desktop and alternate cds, and all the 'tricks' and howtos on the web. It sees the drives and the partitions but depending on the process or howto i use it stopped at different spots, grub, dmraid, etc. If anyone knows how to do it on my mobo or if anyone knows if feisty is supposed to finally resolve the issue please let me know. I am not a linux guru, but I am not a fool either. In my opinion if ubuntu ( or linux for that matter ) is to be widely adopted this is a real sticking point. I and others like me are the middle of the road people that can promote linux, but not if i cannot install it on my machine. This should not be that complicated, and my bootable nortons ghost FLOPPY disk can see and utilize these partitions just fine. If anyone can help please let me know. Thanks in advance. Mike S

---

### Post by esaym on 2007-03-22
> **mnnence said:**
>  This should not be that complicated, 

No but you have to understand that the manufacture of the chipset went cheap and implemented a software raid that is maintained by drivers in windows.  Basically it is a gimmick.  You have 2 choices, you can either by a supported hardware solution for around $100 or so, or you can implement software raid using one of the many many native linux methods.

BTW, does the HD activity led on the front of the computer case work for your sata drives when using the 3112 controller?  I have the same controller and the led ligth only works in windows with sata.  I've gotten used to it though.

---

### Post by mnnence on 2007-03-23
When I bulit the machine ? 4 ? years ago i was not able to get the hdd lights to work in windows , but to be honest I didnt really care so I didnt try too hard. Sorry on that one. 

I cannot use the linux software raid because it needs to be a dual ( quad ) boot machine, with windows. And paying for a card when I already paid for the mobo is not going to happen. Like I said it sees the raid array, i do not think it is incapable of doing what i want, i just think noone has sat down and analysed the situation enough or maybe does not think it is important enough. With one of the tips i read i was able to create and format the partitions and load ubuntu step by step up to and including apt-get ubuntu-desktop, then after that i saw failures. So if i can format and partition, load and see the partitions then theoretically this is possible, if maybe only to fix bugs. dmraid says it supports my chipset, and " cheap " it may be, but also is a very popular mobo and a very popular chipset. And like I said, my nortons ghost 2003 FLOPPY DISK can see these partitions and utilize them fine , and if that is capable why is linux not?

---

### Post by esaym on 2007-03-23
I see.  Well good luck.

---

