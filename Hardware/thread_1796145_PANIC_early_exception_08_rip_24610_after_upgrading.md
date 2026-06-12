---
title: "PANIC: early exception 08 rip 246:10 after upgrading from 2 to 4GB RAM"
date: 2011-07-03
forum: Hardware
---

### Post by herc83 on 2011-07-03
Hi,

I upgraded my system from 2GB to 4GB of RAM and now I can't boot into my Ubuntu :(

My system is:
motherboard: Intel DQ35MP with latest BIOS
cpu: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz
memory now: 2 x 2GB Kingston 800MHz KVR800D2N5K2/4G
memory before: 2 x 1GB Kingston 800MHz

System: Ubuntu Linux 10.04 LTS 64bit installed from Alternative CD
hdd: Full Disk Encryption (that's why I installed from Alternative CD)
uname: Linux hercules-desktop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

* The memory is recognized  by BIOS properly.
* I can enter GRUB menu and choose normal / rescue kernel
* When I try to boot the system I get a dark screen for less then a minute and after that a small message:
PANIC: early exception 08 rip 246:10 ffffffff81037abc cr2 0
and that's it.
* removing one dice (leaving 2GB) removes the problem, but that's not a solution.
* I was trying to boot from: Ubuntu 10.04 Alternative CD 64bit and it failed even without error message.
* I was trying to boot from: Ubuntu 11.04 Desktop CD 64bit and it failed even without error message.

Any ideas? Hints? Where to look next?

---

### Post by ajgreeny on 2011-07-03
Have you tried running memtest86+ from the grub menu?  Leave it running for several hours, overnight if possible, then see if any errors are noted bottom right of the screen.

It sounds as if you have either one faulty memory chip, or there is an incompatibility between the two chips, which can happen even when both will run fine on their own.

---

### Post by herc83 on 2011-07-03
THX for reply.

1. I did run memtest from CD and it started quite OK. I didn't run it for longer than few minutes cos I just wanned to check will it start or not. I can't run it longer at the moment. I got project to finish and that's what extra ram was for...

2. I bought a special double-package designed to be installed in dual-channel configuration so I doubt memory is the problem. I also have no problem with system until it boots. But I'll try to test the memory tomorrow in a different PC.

---

### Post by ajgreeny on 2011-07-03
I suggest you do the test in the machine where you have seen the problem as it could be a memory-chip seating problem as well as the chips themselves.

---

### Post by movieman on 2011-07-03
Another possibility is a BIOS bug which doesn't remap the high memory properly; I had a similar problem when I put 4GB into my AMD system because the BIOS and OS disagreed about whether the memory had been remapped. I had to install a new BIOS to fix it.

If I remember correctly, before the BIOS fix I could boot OK so long as I used a boot command line switch which limited the system to 4GB of RAM so it didn't try to use the remapped memory area. It just meant I lost about 512MB of memory that should have been remapped above 4GB.

---

### Post by herc83 on 2011-07-04
Hi!

Few more facts:

1. I installed completely different memory modules in configuration 4 x 1GB and I get the same error :(
2. I installed 3x1GB and it works!

4GB limit for memory on Ubuntu? Sounds funny :)

3. I installed my new modules in different computer and it works.


So it looks like Intel DQ35MP and Ubuntu with 4GB ram is the problem. Any help?

---

### Post by movieman on 2011-07-04
Try adding mem=4096M on the kernel boot command line; that should prevent it from trying to access remapped memory. You won't get the full 4GB, but should get around 3.5GB.

---

### Post by herc83 on 2011-07-05
I tried mem=2048M and it didn't helped :( But I'll try that again cos I'm not 100% sure did I add "M" at the end :)

Anyway, after adding and removing memory again and again my computer died completely so I can't do any more tests at the moment :(

---

### Post by herc83 on 2011-07-05
PROBLEM SOLVED!

New power supply did the trick:) 

Yeah, really, the power supply!

Old one, after 3 years of 16~18h per day work, said goodbye.

---

