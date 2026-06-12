---
title: "foomatic-rip pegs the cpu"
date: 2008-10-22
forum: Hardware
---

### Post by drubdrub on 2008-10-22
Environment:
[LIST]
[*]Hardy, 8.04
[*]HP Pavillion a1150y
[*]Intel P4, 2.8GHz, dual core
[*]4GB RAM
[*]Printers shared on an XP system
[/LIST]

foomatic-rip is at the top of the top() output consuming 90%+ of the cpu.  System Monitor shows both cores pegged at very close to 100%.  One is at 100% while the other goes to approx 75%.  Then the 2 cores switch load profiles e.g. the second goes to 100% while the first is at approx 75%.

If foomatic-rip is killed, the load on both cores goes to around 15%, which is much closer to normal.  foomatic-rip automagically restarts within a couple minutes, and exhibits the same behavior again.

ps() shows:
lp       20919 20911  0 09:51 ?        00:00:00 [foomatic-rip] <defunct>

The trigger for this behavior seems to have been my attempt to print to an HP 8150, shared on an XP system.  Had not previously seen the behavior.

What the hell?  What is appropriate resolution?  How is the process restarted?  How can the restart be prevented?

---

### Post by eatmo on 2008-11-04
I encountered the same problem when I tried to print to a smb shared HP LaserJet 1022 (Foomatic/foo2zjs). Cancelling the print job seemed to fix it.

---

### Post by servant74 on 2009-08-04
Same issue for me on my Dell D600 laptop with 8.04LTS

---

### Post by warlocksss on 2010-04-06
i had the same issue... i fix it stopping/canceling "print test page" on Printer Config.

Go to System->Admin->Printers

... then ... Select your printer, under Configuration Tab cancel "Print Test Page"... it was on.

 it works for me... 

I don't  know why, but "print test page" was activated but it wasn't doing anything.

-------------------- sorry 4 my bad english ---------------------

---

