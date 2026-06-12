---
title: "X86_64 recursive rebooting on upgrade to 9.10 server"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by hsnewman on 2009-11-01
I had x86_64 server running on my Dell T105 with nvidia 9400GT card.  Upon upgrade, it recursively crashes/rebooted after the black screen with the Ubuntu emblem on it.  

So I reinstalled, using x86_64 9.10 Ubuntu.  Installation completed normally.  Upon reboot, it does the same: recursively crashes/rebooted after the black screen with the Ubuntu emblem on it.

I went into grub and booted into recovery mode.  I can get to the command line.  I looked in the logs and don't see anything.

Any ideas on solutions? 
Thanks in advance.

---

### Post by hsnewman on 2009-11-01
Added dmesg and syslog
Harris

---

### Post by hsnewman on 2009-11-01
Found it, the grub line needed the splash statement removed.
Whew.
Ubuntu rocks!

---

