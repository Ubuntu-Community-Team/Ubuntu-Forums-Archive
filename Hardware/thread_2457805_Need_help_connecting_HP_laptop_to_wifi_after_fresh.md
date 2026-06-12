---
title: "Need help connecting HP laptop to wifi after fresh install of 20.04 lts"
date: 2021-02-09
forum: Hardware
---

### Post by jmichaels29 on 2021-02-09
Need help connecting HP laptop to wifi after fresh install of 20.04 lts

There is no "system menu" or should I say no wifi option in menu at top right

There doesn't appear to be a button on the function keys to turn on wifi

I installed "additional drivers" and rebooted - no luck

fyi It worked before the fresh install (after I installed an SSD).  Computer is the HP Pavilion 17-g161us.  HP did a wifi upgrade/fix years ago.  I changed little battery and computer reverted back to factory bios on first boot up.

---

### Post by jmichaels29 on 2021-02-10
Solved with:

sudo apt-get install --reinstall bcmwl-kernel-source

---

