---
title: "Froze with motherboard tone, 3 beeps on boot"
date: 2008-09-02
forum: General Help
---

### Post by Solidcell on 2008-09-02
So for the last week or so, my computer has been freezing, and upon boot, I get some CMOS checksum error and I have to press F1 to continue.  I just got back from a vacation and now the problem is different.  Now when it freezes (it only froze once since I got back) it freezes with the motherboard making a constant sound (like a beep that never ends).  So I held the power button and restarted it, but now it gives me 3 beeps, which is supposed to mean there's a problem with the RAM.

Are the two problems I've had related (the freezing with the CMOS checksum error and the freezing with the tone and 3 beeps)?

Thanks for any help.

---

### Post by Loaded.len on 2008-09-02
Pull all the ram and fire it up... you should hear the beep code for no DIMM detected.  If it's the same as what you hear with the RAM in, then you can bet you have a problem either with the RAM itself, or the socket. (my money's on the RAM, however sockets fail too...in fact you can get RAM beeps when anything goes wrong on the whole of the memory bus, but let's start with the obvious things first.) 

Next - try the RAM individually in different slots to see if you can reproduce the problem.  If your computer won't post at all, then I'd suggest removing all the expansion cards as well, just to rule them out of the equation.

---

### Post by bobbob1016 on 2008-09-02
Loaded.len beat me to it, it's probably the ram.  If that doesn't work, try replacing the CMOS battery, usually a watch battery, CR-2032.  You can get that at radioshack or somewhere, just pop the old one out carefully.  They cost like $5, not sure outside the US though.  It COULD be a loose IDE cable or something, and it doesn't want to give it full power or a full read since it might damage it, but that isn't likely, and I haven't seen it, although I don't boot machines with loose plugs.

Edit:  You didn't try flashing the bios recently, did you?  That could be it too...

---

