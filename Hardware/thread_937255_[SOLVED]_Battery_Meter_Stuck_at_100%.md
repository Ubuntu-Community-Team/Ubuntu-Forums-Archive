---
title: "[SOLVED] Battery Meter Stuck at 100%"
date: 2008-10-03
forum: Hardware
---

### Post by drydzewski on 2008-10-03
I use Ubuntu 8.04 on a compaq nc6000 laptop.  My battery meter used to work but is now stuck at 100%.  

The battery meter used to work but at some point got stuck at a particular value (don't remember what).  So, I removed the battery while the laptop was turned on (went to 0%) and then put it back in (went to 100%).  Since the battery had been charging for a while, I thought the problem was fixed but unfortunately it has been stuck at 100% ever since (been like this for several months).  

I learned the acpi command during my research into the problem.  That has different issues.  If I use the acpi command it will give a time left in charge that at first appears to be correct but as the battery discharge gets closer to 0, it slows down.  For instance, acpi may be at 4 seconds left for 5 minutes and then it changes to 3 seconds left (I was typing the command every 30 seconds or so during this test).   

I flashed the BIOS to the latest version using a bootable CD that I created.  That had no effect on the problem.  

I have no idea what to do next?  Is there some trouble shooting that I can do?  I see that there are some 3rd party battery managers in the Package Manager, should I try one of them?  Should I post this as a bug?  

Other than this small problem, I think Ubuntu is awesome.  

Thanks in advance,
Dan

---

### Post by drydzewski on 2008-12-08
Update.

I installed the new version of Ubuntu (8.10) and the battery meter is still stuck at 100%.  Since I have already flashed the BIOS to the latest version, I have to conclude that it is a hardware issue.  

For anyone who has a similar issue, try running Ubuntu off the installation CD.  If the problem persists when booting from the Ubuntu CD, then your issue is almost certainly a BIOS issue, or a hardware issue.

---

