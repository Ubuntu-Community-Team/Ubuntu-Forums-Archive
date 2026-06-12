---
title: "Its offical. LSI Mega&quot;fakeraid&quot; and alternative CD does not work"
date: 2009-03-19
forum: Hardware
---

### Post by Friday on 2009-03-19
I gave up. Completely
During install, the fakeraid array comes up as /dev/dd-something-1000

After install, Grup still looks for /dev/dd-something-1000
but, now, the kernel sees the fakeraid as /dev/dd-something-1100
Next boot, the kernel sees /dev/dd-something-1200, even though grup is still looking for 1000. 

THe numbers keep going higher with each reboot, and you have to adjust the grub during the bootup process. 

Any solutions? Or, does linux still need work?

---

