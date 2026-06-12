---
title: "EDAC error in syslog"
date: 2016-10-29
forum: Hardware
---

### Post by Manu_b on 2016-10-29
Hello,

edit: forgot to specify ubuntu release : 16.04


I'm facing an issue with EDAC memory error reporting. The hardware is a dell workstation T7400. I'm using riser boards to use 16 dimm modules arranged in QDR.

I noticed the following line every 1 second in /var/log/syslog :
 EDAC MC0: 1 UE Read error on mc#0branch#0channel#0slot#0 or mc#0branch#0channel#1slot#0 (branch:0 slot:0 page:0x0 offset:0x0 grain:8 - Bank=0 Buffer ID = 0 RAS=0 CAS=0 Err=0x800 (Non-Aliased Uncorrectable Patrol Data ECC))
(always the same memory channel/slot/branch/etc...)

From what I found here and there, it should mean that one memory module is having an issue. Fine, I do have few spares, so I'm trying to identify which memory module is deffective.

So I started some testing. First I remove the riser cards to use the DIMM slot on the M/B (so I will avoid any issues if the problem comes from the riser boards).
The memory installed/to be tested are :
group1 : 4 x 1GB DIMM ECC FB 2Rx8
group2 : 4 x 2GB DIMM ECC FB 2Rx8
group3 : 4 x 2GB DIMM ECC FB 2Rx4
group4 : 4 x 2GB DIMM ECC FB 2Rx4

So I started testing group1 in the M/B, BIOS is ok (sees all memory modules) and after boot, no entry (no entry related to EDAC error) in the /var/log/syslog.
Then I started testing group2, same, no errors.

When I tested group3, the error immediately appears in syslog after boot. Sinc ethe message refers to what seems to be the first memory module, I swapped it with a module from group4 (exactly same memory module ref/specs as group 3).
After reboot, the error is still there. So I continued swapping dimm2, 3 and 4, and still the error appears in syslog.

So I'm puzzled here ! does that mean that ALL 8 modules (from group 3 and 4) are deffective ? And why does it always report the error in the same slot whatever the memory module from group 3 or 4 is in?

Since slot 1-4 have been tested ok with memory from group 1 and 2, I concluded that there should not be any hardware issue with the M/B (cpu, memory controller, dimm slots).

The only thing I see is that Group3 and 4 are the same memory type with 2Rx4 org. while memory group 1 and 2 are using 2Rx8 memory org.

Now, these memory modules have been tested on another machine (690 workstation, wich use a different memory controller), and no error are found on this machine.

The issue is not about mixing 2Rx4 and 2Rx8 as 2Rx4 alone does trigger the error.
This memory type should be supported : there's no mention of NOT to use 2Rx4 modules, bios does not complain and even the integrated diag tool, sort of memtest, reports no memory error. (and by the way memtest+ does not find any error).

Also Memtest+ does not report any error.

So, should I just ignore those errors or should I worry ? for me that sounds more like a bug with EDAC error reporting with this setup (cpu/memory controller/memory module type). I also tries upgrading the BIOS (from A03 ro A11 which is the most recent), with no impact.

---

### Post by yvesdm3000 on 2016-12-21
If you look at the documentation of your system, it states that you can't mix 2Rx4 and 2Rx8 modules. I have a similar system and I had to remove the 2Rx4 modules when I added the rather big 2Rx8 ones.

---

