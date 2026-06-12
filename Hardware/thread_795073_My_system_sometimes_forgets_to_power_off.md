---
title: "My system sometimes forgets to power off"
date: 2008-05-15
forum: Hardware
---

### Post by kissg1988 on 2008-05-15
I'm running Ubuntu 8.04 on a Prestigio Nobile 150 laptop, kernel version 2.6.24-16-generic. The problem is, that the system doesn't shut down correctly. The last message I can see on the console is:

halt: Unable to iterate IDE devices: No such file or directory

After this, one of the following things happen:

1. The system powers off after half a minute or so (chance: about 10%)
2. Nothing happens, I see the message above on the screen and my system would keep running forever. I have to switch it off by pressing the power button for at least 5 seconds. (chance: about 90%)

This problem is quite strange to me, because I have never had any issues with this in any previous releases. The DSDT of my system is bug-free, I checked by disassembling and then recompiling it. The Intel AML compiler indicated no errors.

My system turns off correctly under Windows XP.

Any ideas?

---

