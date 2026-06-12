---
title: "ASUS P5W DH Deluxe"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by abrazafi on 2009-02-04
Hi All,

I have ASUS P5W DH Deluxe as MotherBoard with Intel Core duo CPU.
I just finished to install Kubuntu 8.10 ... Found many times that
my system hanging/freezing a lot.

Then after powered cycle my system, I got the following 
message on my screen:

AMIBIOS (C) 2006 American Megatrends, Inc.
ASUS P5W DH Deluxe ACPI BIOS Revision 1305
CPU : Intel (R) Core(TM) 2 CPU 6300 @ 1.86Ghz
Speed : 1.86 GHz Count : 2

Entering SETUP ..
Press F8 For BBS POPUP
PC2-5300 Dual Channel Interleaved
Initializing USB Controllers .. Done
2048MB
USB Devices(s): 1 Keyboard, 1 Mouse, 1 Hub, 4 Storage Devices
Auto-Detecting Pri Master..ATAPI CD-ROM
Auto-Detecting Pri Slave...ATAPI CD-ROM
Auto-Detecting 3rd Master..IDE Hard Disk  <-- wrong! connected on SATA1 
Auto-Detecting 4th Master..               <-- system hanging here
                                              forever


Note that:

1- when I unplugled the HD SATA1, the 3rd Master 
message disappeared and the system is still hanging on 
the 4th Master (see above).

2- I tried to boot with the MotherBoard CD (Intel 975x Series)
without any progress, still hanging on the $th Master (See above)

Question's

a)- What does it mean ? My Motherboard is dead or just a Bios 
issue ?

b)- how can I resolve this issue.

Any suggestion will be welcomed.

Thanks,
Don.

---

### Post by dabl on 2009-02-04
The SATA connectors are not all the same.  I don't know your P5W DH mobo, but on a P5Q Pro, one of the connectors is orange -- that's the one to use first.  You probably need to get out flashlight and look for "SATA 1" or something like that stenciled beside the connectors.

Also, in BIOS, the SATA channel should have a "mode" -- you need to set it to AHCI, unless you need to boot Windows too.

---

### Post by abrazafi on 2009-02-04
dabl,

>You probably need to get out flashlight ...
You are right, the MOBO has 3 SATA connectors, one of them 
is red which is the SATA1. Note that this machine was working
like rocket since last night. So I didn't change any connection.
Just after the hard power cycle, my system became freezing and
waiting for this 4th Master...


>Also, in BIOS, the SATA channel should have a "mode"
I cannot even access the BIOS, the <DEL> command is inactive
and the system is freezing...

Note that the following line seems to me wrong:
          Auto-Detecting 3rd Master..IDE Hard Disk 
because my HD is Serial SATA not IDE!

Many thanks anyway,
Don.

---

### Post by dabl on 2009-02-05
> **abrazafi said:**
> dabl,

I cannot even access the BIOS, the <DEL> command is inactive
and the system is freezing...



That's a bad thing!

Have you tried totally unpowering it for a few minutes?  Shut it down and pull the power plug out of the wall for 10 minutes, then plug it back in and try again.

You have to have a correctly functioning BIOS, before there is any hope of booting the OS properly.  :?

Also Don.  :)

---

### Post by abrazafi on 2009-02-11
Hi All,

I gave up and I sent the mobo to asus because
it is still under warranty.

Many thanks for your helps.
Don.

---

### Post by abrazafi on 2009-04-10
Hi All,

The ASUS took times and sent me a new mobo. 
Everything works fine and I upgraded to kubuntu 8.10

Thanks,
Don.

---

