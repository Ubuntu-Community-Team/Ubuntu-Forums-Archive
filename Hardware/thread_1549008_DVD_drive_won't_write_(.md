---
title: "DVD drive won't write :("
date: 2010-08-09
forum: Hardware
---

### Post by winx2linx on 2010-08-09
Hi guys,

The DVD drive in my laptop does not erase nor write to any RW media in Ubuntu 10.04. I have tried different brands of CD and DVD RW media but the problem remains. Tried reinstalling Brasero, even installed K3B without any success. No success with a fresh reinstall of the OS.
The same drive writes the same data on the same media in OpenSUSE 11.3 (KDE) and Windows Vista so no problem with the drive here. Guess its related to the OS. Anyone have a clue about this please?

Thank you.

---

### Post by clrg on 2010-08-09
Please show me the output of

```
wodim -v -scanbus
```

---

### Post by mziskandar on 2010-08-09
I'm having the same problem on my Samsung SH-182d (previously ~ 9.04, burned well). Will post the result when I get back to Ubuntu.

---

### Post by winx2linx on 2010-08-09
> **clrg said:**
> Please show me the output of

```
wodim -v -scanbus
```


Hi,

Here's the output of the command:
---------------------------------------------------------------------
TOC Type: 1 = CD-ROM
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
Driveropts: 'burnfree'
SCSI buffer size: 64512
scsibus1:
    1,0,0    100) 'MATSHITA' 'DVD-RAM UJ880AS ' '1.00' Removable CD-ROM
    1,1,0    101) *
    1,2,0    102) *
    1,3,0    103) *
    1,4,0    104) *
    1,5,0    105) *
    1,6,0    106) *
    1,7,0    107) *
----------------------------------------------------------------------

Thanx.

---

### Post by mziskandar on 2010-08-10
My output for:
> wodim -v -scanbus

is quite the same..
> 
TOC Type: 1 = CD-ROM
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
Driveropts: 'burnfree'
SCSI buffer size: 64512
scsibus1:
	1,0,0	100) *
	1,1,0	101) 'TSSTcorp' 'CD/DVDW SH-S182D' 'SB07' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *


---

### Post by clrg on 2010-08-10
This might be helpful:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/531901]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/531901")

---

### Post by morrie on 2010-10-15
I have the same on a fresh install of 10.04 64-bit.  I am afraid to say, the post provided is quite a bit over my head (plus it appears to only apply to that user's specific situation).

Is there anyone that has experience with this that can tell us what to try?  I fail to see the logic in "pulling out wires" of a clean installation as a "bug fix"  If that's a bug fix, then I'm a Windows user.  This post does not even resolve the bug (since March) but passes the buck over to another esoteric package.  Not helpful, unless you're an extremely-gifted read-between-the-lines type.

So, I guess we're waiting for them to fix the bug in hal (whatever that is)?

---

