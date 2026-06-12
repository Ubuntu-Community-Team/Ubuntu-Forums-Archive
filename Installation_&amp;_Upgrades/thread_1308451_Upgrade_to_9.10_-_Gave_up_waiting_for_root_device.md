---
title: "Upgrade to 9.10 - Gave up waiting for root device"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by gcmelzi on 2009-10-31
I just upgraded my system and I'm now stuck at reboot. 
Here the details:

CPU: Celeron 400
Memory: 320k
OS upgrade: Xubuntu, from 9.04 to 9.10
Dedicated disk for /home
Upgrade: took some time, but no problems till reboot.
At reboot:
Usplash: Setting mode 1024x768 failed
Usplash: using mode 800x600
Gave up waiting for root device, Common problems: …
-…
-…
ALERT! /dev/disk/by-uuid/1b0ff99d-e635-47fa-b01a-38ec073369d6 doen not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.1.13.3-1ubuntu7) buil-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

And now?
Could someone kindly suggest what to do, please?

Thanks in advance.

---

### Post by gcmelzi on 2009-10-31
At GRUB
e
edited the KERNEL line changing 
root=UUID.....
with
root=/dev/sda1

Now the screen resolution ...

---

### Post by Ces on 2009-11-02
:D Thank you! This solution was exactly what I needed.

---

### Post by rvachtl on 2009-11-02
It helped me too, many thanks!

---

