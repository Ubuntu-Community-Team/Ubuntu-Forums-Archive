---
title: "Cannot suspend with Compaq Presario CQ40"
date: 2009-07-12
forum: Hardware
---

### Post by jono_nz on 2009-07-12
Hi guys, I'm running Ubuntu 9.04 on a Compaq CQ40, and I'm having issues with suspending Ubuntu. I've been wading through other threads in this forums with similar problems with little success. 

Firstly, I should point out that I'm not very familiar with Linux; I'm still mostly an XP user, with that running on my desktop which I primarily use. 

In any case, I've found out (by using the s2ram and s2disk commands) that I can suspend to disk, but not to ram. If I were to suspend to disk, everything works fine. However, if I suspend to RAM, and I try to restart my laptop, it'll run into a bunch of errors displaying on console, displaying the following messages:

```
ata5/1: irq_stat 0x00000040, connection status changed
ata5/1: SError: { DevExch }
ata5/1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
```Where the ata5/1 would alternate between ata5 and ata1 on each iteration of the error messages.

I've read that in other threads that others have made that their hard drives are failing, but don't think this should be the case as I run Vista on a separate boot which suspends perfectly fine. Similarly, I don't run into any other hardware issues if I just avoid suspending my laptop.

I've been living with this problem for a while now, but I need to have my suspend feature! I miss my days of simply closing the laptop lid and leaving it to suspend on its own and knowing that all my work will still be there when I return in the morning.

Please help a desperate amateur programmer, who avoids working directly on his laptop as a result of this issue and instead uses Putty, Xming  and (Microsoft's) notepad on his desktop!

Thanks in advance, and any input is greatly appreciated. Cheers!

---

### Post by jono_nz on 2009-07-13
Shameless self-bump.

Perhaps the more appropriate question would be, is it possible (and how) to change it so that the default suspend type that Ubuntu with the one specified in the Power Management window to suspend to disk rather than ram?

Thanks again!

---

