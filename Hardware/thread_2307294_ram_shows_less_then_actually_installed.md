---
title: "ram shows less then actually installed"
date: 2015-12-23
forum: Hardware
---

### Post by sajil2 on 2015-12-23
hi 
i am using ubuntu 14.04 lts on workstation.i installed 20 gb ram but i checked it shows 2 gb only but if i go in detail it shows i a
instaed 20gb.how do i enble rest of the ram?
dell precision 690 2 xeon processor

* Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Wed Dec 23 14:02:50 2015 from 192.168.0.19
root@ubuntu:~# free -m
             total       used       free     shared    buffers     cached
Mem:          1998       1733        264         41         59       1160
-/+ buffers/cache:        513       1485
Swap:         2044         95       1949
root@ubuntu:~# grep MemTotal /proc/meminfo
MemTotal:        2046440 kB
root@ubuntu:~# sudo lshw -short -C memory
H/W path        Device     Class       Description
==================================================
/0/0                       memory      64KiB BIOS
/0/400/700                 memory      32KiB L1 cache
/0/400/701                 memory      4MiB L2 cache
/0/401/702                 memory      32KiB L1 cache
/0/401/703                 memory      4MiB L2 cache
/0/1000                    memory      20GiB System Memory
/0/1000/0                  memory      1GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/1                  memory      1GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/2                  memory      1GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/3                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/4                  memory      1GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/5                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/6                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/7                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
root@ubuntu:~#
root@ubuntu:~#

---

### Post by gordintoronto on 2015-12-23
That might be due to installing the 32-bit version of Ubuntu. Run this command: uname -a

---

### Post by 1clue on 2015-12-23
+1 on 32-bit version, you want 64-bit on anything that will accept that much RAM.

It also appears that you have two dimms out of order.  On every motherboard I've seen you need to have banks of like products for best performance, you have the middle two, 3 and 4, reversed.

---

### Post by Bucky Ball on 2015-12-24
> **1clue said:**
> +1 on 32-bit version, you want 64-bit on anything that will accept that much RAM.

It also appears that you have two dimms out of order.  On every motherboard I've seen you need to have banks of like products for best performance, you have the middle two, 3 and 4, reversed.

And +1 to all of this again. You want 64bit and make sure your RAM sticks are paired correctly (the slots are normally coloured in pairs or numbered. My motherboard uses slots 1 and 3 for one pair, 2 and 4 for another.

Silly question perhaps, and slightly off-topic, but you are positive your motherboard can handle that amount of RAM ... just asking. :)

---

### Post by Vladlenin5000 on 2015-12-24
And another +1...

[Dell Precision 690 Workstation]("http://www.dell.com/downloads/global/products/precn/en/spec_precn_690_en.pdf") supports up to 64GB of RAM:

>  Up to 64GB quad-channel architecture DDR2 Fully Buffered DIMM 533 and 667MHz ECC memory; Up to 16 DIMM slots; 1KW chassis required for memory expansion greater than 32GB (greater than 8 DIMM slots)



---

### Post by sajil2 on 2015-12-24
hi thanks for responding . actually this is  ubuntu 64 in the system.what can i do to accept all the ram?
root@ubuntu:~# uname -i
x86_64
root@ubuntu:~#

---

### Post by Bucky Ball on 2015-12-24
Have you swapped slot 3 and 4 over? 

Please provide the output of 'uname -a', as requested earlier. :)

---

### Post by sajil2 on 2015-12-24
ok here is out put i pulled out 1 gb sticks.

root@ubuntu:~# free -m
             total       used       free     shared    buffers     cached
Mem:         16045        699      15346         35         46        289
-/+ buffers/cache:        363      15682
Swap:         2044          0       2044
root@ubuntu:~# lshw -short -C memory
H/W path        Device     Class       Description
==================================================
/0/0                       memory      64KiB BIOS
/0/400/700                 memory      32KiB L1 cache
/0/400/701                 memory      4MiB L2 cache
/0/401/702                 memory      32KiB L1 cache
/0/401/703                 memory      4MiB L2 cache
/0/1000                    memory      24GiB System Memory
/0/1000/0                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/1                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/2                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/3                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/4                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/5                  memory      4GiB FB-DIMM DDR2 FB-DIMM Synchronous 667
/0/1000/6                  memory      FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz
/0/1000/7                  memory      FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz
root@ubuntu:~# uname -a
Linux ubuntu 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by 1clue on 2015-12-24
In your computer user's manual, it says your bios has a setting "POST Behavior -> OS Install" which needs to be turned off.  If it's on it limits the memory to 2gb.

As well, your system seems to have banks of 4, I haven't found the recommendation but generally speaking you want all modules in any bank to be identical size and speed, or you'll suffer performance consequences.  Also traditionally you put the largest/fastest modules in the first bank.

Do you have riser cards in the white bank?  If so, then the black bank should be empty.

While you're in the BIOS section, can you tell if the BIOS recognizes all the memory?  And can you tell if the exact CPUs you have are 32 or 64-bit?  From the way the manual is worded it might be possible to have 32-bit CPUs.

---

### Post by sajil2 on 2015-12-24
thanks for resonding there is no riser in any slot but i will double check bios for os install on off thing
thanks

---

### Post by sajil2 on 2015-12-24
hi
i checked bios yes both cpus are 64bit technology.but i couldnt find post behaviour to install os off and on.

---

