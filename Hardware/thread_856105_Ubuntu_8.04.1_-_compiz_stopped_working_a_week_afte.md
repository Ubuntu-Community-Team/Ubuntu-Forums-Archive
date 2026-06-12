---
title: "Ubuntu 8.04.1 - compiz stopped working a week after the initial install"
date: 2008-07-11
forum: Hardware
---

### Post by ilian on 2008-07-11
Hi!
2 weeks ago I switched from openSuSE to ubuntu I seem to have some problems.

I have Sony VGN-SZ340P notebook. It has 2 graphics cards (an intel 945 and nvidia 7400go), which can be switched with a button.

At first almost everything worked out of the box, but then for no apparent reason, after a reboot compiz stopped working. I decided an update must have broken the intel driver and switched to the nvidia card.
On the next reboot the setup screen came up, it set my card up, but 3D acceleration was not working either. I tried installing the nvidia binary driver, but it seems I have no C development environment installed.

- So, is there an easy way to get compiz working again (short of reinstalling)?
- Is there an application similar to YaST2, that I can use to change system settings, or at least video settings?
- How do I install all packages needed to compile a kernel driver?
- Does ubuntu have a "hardware profiles" feature like openSuSE - I do not want to have to setup my video every time I switch cards?

Thanks a lot!
-Ilian

---

### Post by ilian on 2008-07-12
For anyone that may have the same problem. Here is the solution:

The problem was caused by a kernel update
- The update to 2.6.24-19-generic breaks x11-intel support.

If anyone has this problem - simply boot your old kernel.

To be on the safe side - disable the update! It does not seem these go through adequate QA process before being released.

---

