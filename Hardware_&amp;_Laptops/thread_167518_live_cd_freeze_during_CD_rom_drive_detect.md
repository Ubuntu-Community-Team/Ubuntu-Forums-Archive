---
title: "live cd freeze during CD rom drive detect"
date: 2006-04-28
forum: Hardware &amp; Laptops
---

### Post by fatalxception on 2006-04-28
Hi,
i use a AMD64 1800+ with a MSI RS480 mobo with a samsung CD writer and a Samsung DVD ROM. My hdd is a 120GB SATA. I'm currently using winxp.
i find both the live cd and install cd freeze during the hardware detection stage while loading the cd rom module. i've tried the noapic and nolapic commands (as given in the help menu). didnt work..
been trying to get this to work for quite some time now

CD rom was ordered from shipit.ubuntu.org.

rgds

---

### Post by WillemKeizer on 2006-04-28
Hi,

I had the same problem on my laptop; with ubunto and also with SuSE. Try booting with acpi=off (in Ubuto type behind boot: 'linux acpi=off'. Then the power controls are not loaded. Worked for me. Now I have to figure out how to install acpi...

Good luck, Willem

---

### Post by fatalxception on 2006-04-29
Hey Willem,
i tried acpi=off. no go :(
the place where it gets stuck is when it says:
Detecting hardware to find CD ROM. ---> 86%
Loading IDE-CD for Linux ATAPI CD-ROM.
no idea abt how to solve this. i had installed mandrake quite sometime back with the same two drives that i now use.. dunno wat to do..
thx,
Aanand

---

### Post by MediaHound on 2006-06-24
Similar problem. 
Installation is stuck at 86% of "Detecting hardware to find CD_ROM drives" ... 
Loading module 'ide-cd' for 'Linux ATAPI CD_ROM'... 

Had to remove power supply to unstick it. :p 

This one is a dusty AMD K6-2 @ 400MHz 512, 8.5GHDD :D 
HP CD-Writer Plus 8000 series as the primary master and some various DVD drive as the primary slave. IDE secondary master is the 8455MB HDD.

It's a fresh ubuntu 6.06 downloaded from a mirror a couple of hours ago. 

All replies considered helpful. :)

---

### Post by MediaHound on 2006-06-24
I should have continued on with my search before pausing to reply to this thread. 
Here's a chock-full-of nuts thread on the very topic. 
I'm about to dive into it some more. 
Wish me good luck. 
[http://www.ubuntuforums.org/showthread.php?t=76482](http://www.ubuntuforums.org/showthread.php?t=76482)

---

### Post by MediaHound on 2006-06-24
So I left it overnight to no avail, it never got past that step on its own.

Retried, but this time I typed "linux acpi=off" at the prompt, and it worked. 

/clicks install 
;)

---

