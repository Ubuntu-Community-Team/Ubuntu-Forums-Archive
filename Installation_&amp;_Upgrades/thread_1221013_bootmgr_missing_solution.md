---
title: "bootmgr missing: solution"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by Motomouse on 2009-07-23
The error message **bootmgr missing** after selecting Vista in your freshly installed grub menu indicates that probably the update-grub script was not able to create a valid boot entry for your Vista bootloader during the grub installation process. 

You have two options to solve this:

[LIST=1]
[*]Use the system repair option of your Vista Install DVD to repair the Vista boot process (loosing your grub boot menu)

[*]Create manually a valid entry for your Vista bootloader in the menu.lst file of your grub installation
[/LIST]

(On my system the grub installation detected a vista system on (hd 2,0) and tried to map (hd 2) to (hd 0) - without success. A manual entry according to the menu.lst comments did the job on my box:


failed automatical entry:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Windows Vista (loader)
rootnoverify    (hd2,0)
savedefault
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

working manual entry:

```
title           Vista (hd0,0)
root            (hd0,0)
makeactive
chainloader +1
```

Regards
Motomouse

---

