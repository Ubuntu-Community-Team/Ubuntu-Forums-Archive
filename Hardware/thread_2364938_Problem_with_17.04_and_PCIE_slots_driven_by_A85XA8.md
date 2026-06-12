---
title: "Problem with 17.04 and PCIE slots driven by A85X/A88X chip on Gigabyte motherboards"
date: 2017-06-29
forum: Hardware
---

### Post by fastpoke on 2017-06-29
Under 13.10, I was using 5 PCIE slots with a GA-F2A88X-D3H and 6 slots with a GA-F2A85X-UP4 (both Gigabyte boards).  Due to end of life, I upgraded these systems to 17.04.  At that point, only 4 slots on each board worked.  If I leave the cards in the remaining slots the install ISO won't even boot, and I get IOCTRL loop timeout errors on the console before the system crashes, if I'm lucky.

Of course, I'm mining, and the slots are connected to R9 290s.  I've seen lots of posts about PCIE's not working but nothing that mentions what I notice.

It seems that the slots that stop working are the ones connected to the A85X or A88X chip.  The ones directly connected to the cpu still work.

I have verified that the problem isn't hardware.  If I have all the slots filled, 17.04 won't boot, but if I boot from 13.10, everything runs fine.  I installed 14.041 and have the same problem.

I suspected a driver issue, but when I run this command:

sudo dmidecode | grep "PCI" 

I get the following:
**GA-F2A85X-UP4 **(I have 2 of these mobos and they show the same problem) 
       Type: x16 PCI Express
        Type: x1 PCI Express
        Type: x8 PCI Express
        Type: x16 PCI Express
which is missing the PCIEX4 && PCIEX1_3 slot


[B]F2A88X-D3H
[/B]        Type: x16 PCI Express
        Type: x1 PCI Express
        Type: x8 PCI Express
        Type: x16 PCI Express
which is missing the x4 PCIE slot

Here are the block diagrams of both these boards.  The missing PCIE's from the above list match the slots that don't work if I put a GPU in them, and they are the ones attached to the A85X and A88X respectively.

[IMG]http://i.imgur.com/MIxqQgO.png[/IMG]
[IMG]http://i.imgur.com/MkurDW3.png[/IMG]

In both cases, the PCIE slots connected to the A8*X chip don't work.

Is this a known problem/limitation?  Is there a kernal patch that addresses this problem somewhere?

Note: this doesn't seem to be a problem with ASUS.  On the ASUS A88X-PRO, dmidecode gives me:
        Designation: PCIEX1_1 
       Type: 32-bit PCI Express
        Designation: PCIEX16_1
        Type: 32-bit PCI Express
        Designation: PCIEX1_2
        Type: 32-bit PCI Express
Designation: PCIEX16_2
        Type: 32-bit PCI Express
Designation: PCIEX16_3
        Type: 32-bit PCI Express


which matches the PCIE slots the mobo has.  I haven't had the time to investigate this board further.

---

### Post by dessertguru on 2017-07-23
Have you found a resolution or reason to this issue yet? I'm having the very exact same problem but on a different OS platform.

---

