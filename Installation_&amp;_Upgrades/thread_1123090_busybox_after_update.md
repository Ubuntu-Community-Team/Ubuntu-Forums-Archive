---
title: "busybox after update"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by mikedmor on 2009-04-11
i update ubuntu jaunty yesterday and when i restarted my computer i got dropped into the busybox shell. Before i updated it required me to reconfigure something because it wasnt letting me update. 

here is what it shows in when i try to boot:

```
Boot from (hd0,0) ext3   XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Starting up ...
Loading, please wait...
udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enought?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 
```

here is what the boot is:

```
uuid XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet
```

i do have a recovery mode but i get the same results when i try to start it as well. But the memtest does work. and my windows xp partition works as well. I cant really afford to reinstall ubuntu because i have LOTS of needed information on there and i have spend days working on getting it just how i want it. is there any way to get my linux to boot again?

if you need more information via liveCD or other means please ask!

thank you

-mike

---

### Post by jejones3141 on 2009-04-12
Check out [http://ubuntuforums.org/showthread.php?t=1120858;](http://ubuntuforums.org/showthread.php?t=1120858;) I had the same problem, and dropping back solved it for me.

---

