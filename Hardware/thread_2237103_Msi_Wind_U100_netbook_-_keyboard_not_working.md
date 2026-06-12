---
title: "Msi Wind U100 netbook - keyboard not working"
date: 2014-07-30
forum: Hardware
---

### Post by Anbog on 2014-07-30
I'm trying to make an old netbook useful again, but for some reason the keyboard doesn't work in Ubuntu. It works in the BIOS, in GRUB and when booting into its old WinXP. Besides standard Ubuntu, I have the same problem when booting live versions of recent Xubuntu, Linux Mint and Fedora, along with Ubuntu 12.04.4. However, the keyboard works fine when booting the old Ubuntu 8.04. I can try more versions to find out when the problem started, if it's helpful for figuring out what the problem is..

After searching around a bit, I've tried playing around with some kernel config via GRUB (hope I'm describing this somewhat correctly - it's new ground to me): i8042.nomux, .dumbkbd, .nopnp and .reset - all without any luck. I also found some reference to suspend/resume cycles getting rid of the problem, but that's not the case for me.

If I connect a USB keyboard to the netbook, that works fine, which helps a lot, but I'm a bit lost on how to proceed. Any suggestions?

---

### Post by Anbog on 2014-07-31
Finally got it working - the solution for me was to update the BIOS to the latest version (10G).

---

