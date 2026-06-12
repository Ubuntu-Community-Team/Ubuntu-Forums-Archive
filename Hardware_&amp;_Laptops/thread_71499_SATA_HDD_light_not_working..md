---
title: "SATA HDD light not working."
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-03
The little light on the case does not work at all with ubuntu.
works in windows.
Anyone know how to activate it?
thanx
p.s it works whe the cd rom is in use but not the SATA hard drive...

---

### Post by skoal on 2005-10-03
hmm, that's interesting.  I would have thought the activity LED was implemented in hardware off of your motherboard, detecting any "activity" across your IDE controller.  That's why you would see that "activity" light during the POST (even on your SATA drive), when separate OS level drivers haven't been passed off yet by the BIOS init process...

However, if you say it does so in Windows, then I would assume it has something to do with SATA drivers treated as SCSI in Linux, and not so in Windows (maybe).  Either way, I thought all that was tied to hardware, independent of any OS or other software.  I dunno...

\\//_

---

### Post by floyd27 on 2005-10-03
.....im not sure either..
it does light when booting but once im in linux its a no go..
Doesnt really matter just though it was weird..but i would like to get it working..

---

