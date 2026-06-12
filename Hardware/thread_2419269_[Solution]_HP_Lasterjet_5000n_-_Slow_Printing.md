---
title: "[Solution] HP Lasterjet 5000n - Slow Printing"
date: 2019-05-19
forum: Hardware
---

### Post by rafaeldejongh on 2019-05-19
So I've been working on this since around 11pm, it's now 8am and finally am around to getting everything configured with the latest Ubuntu LTS release, the problem I mainly had was that my old laser printer a HP Laserjet 5000n was printing super slowly, like it took minutes for it to receive the task and then if the task had multiple pages that as well took several minutes. Where before on windows this was not a problem at all. 

I searched this and various other forums with similar printers to try their solutions out without success, and I think I might just gotten it from some random post that for the person didn't work for his type of printer but for me it did.

So the solution for my problem and the HP Laserjet 5000n printing slowly would be to put the drivers/printer model to:
**HP LaserJet 5000 - CUPS+Gutenprint v5.2.11**

All other drivers that were suggested and installed by default resulted in slow printing, but changing it to this everything worked as it did on Windows.

So this is more of a post for people in a similar situation that I would want to perhaps provide the info for that this drive might actually fix their old LaserJet slow printing issue.

---

