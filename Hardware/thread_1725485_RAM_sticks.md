---
title: "RAM sticks?"
date: 2011-04-09
forum: Hardware
---

### Post by TrumpyNZ on 2011-04-09
Hi there folks,
I've got a Dell Latitude D500 laptop here, this is one of a couple of Dell's I've owned in the past.
It has 512MB of RAM currently installed, what I would like to do is upgrade it to 1024MB by using another 512MB stick of RAM out of an old computer that is no longer working.
Is this possible?
I've never tried to do this before and I was wondering if anyone else here has and what sort of results they got.

Cheers, 
Mike. :confused:

---

### Post by Yellow Pasque on 2011-04-09
Well, it has to be a DDR SO-DIMM (no DDR2/DDR3) and it has to run at the same speed (or better) as the other module. Quick Google looks like the D500 came with PC2100, but don't quote me on that.

---

### Post by prshah on 2011-04-09
> **TrumpyNZ said:**
> I would like to do is upgrade it to 1024MB by using another 512MB stick of RAM out of an old computer

I mix and match old and new memory all the time, with usually good results. Caveats: I usually do this on desktops ; the memories have to be compatible (pin/voltage wise).

If you do try to use the old ram, I suggest the first thing you do after installing it is to use the ram test (memory test / memtest) option in the GRUB menu. Booting an OS with a faulty memory stick can lead to OS corruption (unlikely, but it can happen).

Use memtest for a period of over 6 hours for a clear picture; if you are in a hurry, you should know reasonably certainly within 15-20 minutes.

---

### Post by 3rdalbum on 2011-05-20
> **prshah said:**
> 
Use memtest for a period of over 6 hours for a clear picture; if you are in a hurry, you should know reasonably certainly within 15-20 minutes.

I've had lots of faulty RAM and none of it has failed 15-20 minutes into Memtest; in fact some of it has passed 8 hours in Memtest.

If you're after a quick result, a RAM benchmark in Phoronix Test Suite will crash in a couple of minutes if you have bad RAM.

---

