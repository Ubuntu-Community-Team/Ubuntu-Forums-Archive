---
title: "laptop turns off during restart"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by rocco_d on 2008-02-24
I customized the kernel and init scripts of my ubuntu gusty and only afterwards realized that when I restart the PC, apparently something is left misconfigured and I believe the BIOS shuts it off since it seems to restart after the 'will now restart...' message.

I then reverted to the original 2.6.17.10-generic kernel and added init=/bin/bash and now even after booting with that, pressing ctrl+alt+del shuts down the computer.

I assumed that something with the computer went wrong in the mean time, but the live CD restarts fine. And a few days ago, it used to do from the harddrive as well.

My specs are: core 2 duo + i965.

Any suggestions are welcome.
Thanks

---

