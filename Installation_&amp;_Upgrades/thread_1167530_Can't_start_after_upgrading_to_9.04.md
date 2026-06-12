---
title: "Can't start after upgrading to 9.04"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2009-05-23
If I choose the recovery mode from grub menu to boot, it will stop at



Begin: Wating for root file system ...
Done.
Gave up wating for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - check rootdelay = ...
   - check root=
 - Missing modules (cat /proc/modules; ls /dev)
ALERT: /deve/disk/by-uuid/<some string> does not exist. Dropping to a shell!

BusyBox v.10.2 (Ubuntu 1:1.10.2...) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


<here it appears that the cmputer doesn't respond to keystroke or mouse movement>

What should I do here ?

If I start the normal kernel, it intially give normal booting graphics and texts, then it give you a black screen then stop.

---

### Post by hansdown on 2009-05-23
Hi Physicist.

This thread is perhaps helpful.

[http://www.google.ca/search?q=ALERT%3A+%2Fdeve%2Fdisk%2Fby-uuid%2F%3Csome+string%3E+does+not+exist.+Dropping+to+a+shell!&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ALERT%3A+%2Fdeve%2Fdisk%2Fby-uuid%2F%3Csome+string%3E+does+not+exist.+Dropping+to+a+shell!&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Physicist on 2009-05-24
> **hansdown said:**
> Hi Physicist.

This thread is perhaps helpful.

[http://www.google.ca/search?q=ALERT%3A+%2Fdeve%2Fdisk%2Fby-uuid%2F%3Csome+string%3E+does+not+exist.+Dropping+to+a+shell!&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ALERT%3A+%2Fdeve%2Fdisk%2Fby-uuid%2F%3Csome+string%3E+does+not+exist.+Dropping+to+a+shell!&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

After rolling back the kernel to an earlier revision, it can boot. But at the login screen, the computer does not respond to my mouse and keyboard ? I can't go into command line by Ctrl+Alt+F2 either.

---

### Post by Physicist on 2009-05-24
Anybody encounted same problem ?

---

### Post by hansdown on 2009-05-24
Actually a lot of posts have been made. I can't give you a good answer,

except that 9.04 may not work well with your hardware.

What were you running before?

---

### Post by Physicist on 2009-05-24
I was using 8.04, it was all fine.

---

### Post by hansdown on 2009-05-24
8.04 is very stable. Some information.

[http://www.google.ca/search?q=ubuntu+9.04+upgrade+problems&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=ubuntu+9.04+upgrade+problems&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I hope you get it fixed.

---

