---
title: "Windows Partition is broken, need to reinstall without screwing up Ubuntu"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by G-Dub on 2009-07-02
Hey guys, I haven't used my windows partition for so long that all sorts of stuff is screwed up. Leave it to windows to screw up when you don't even use it. Anyway, there are several games I really want to play and have been unsuccessful at getting ubuntu to run them. How can I reformat my windows partition and reinstall windows without overwriting the GRUB bootloader or messing anything else up.

---

### Post by merlinus on 2009-07-02
You can certainly reinstall windows to its previous partition, but it will definitely overwrite grub.  However, this is very easy to fix.  If you do a search here and/or on google you will come up with thousands of hits.

---

### Post by starcraft.man on 2009-07-02
[Presto.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Just in case. Nothing really special to do, just install Windows and ensure your only writing over the old partition. Then follow directions and GRUB will be back before you know it. Any questions, you can ask in the live CD just by going online.

---

### Post by philcamlin on 2009-07-02
install windows then boot into ubuntu live cd and reinstall grub :)

---

