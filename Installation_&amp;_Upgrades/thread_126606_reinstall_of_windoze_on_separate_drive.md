---
title: "reinstall of windoze on separate drive"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by gpw797 on 2006-02-06
I have dual boot breezy and xp on separate drives. If I reformat XP drive and reinstall XP will I still have grub boot menu and all will be ok? If not please help :)

---

### Post by jasmuz on 2006-02-07
If you reformat your Windows XP partition and reinstall, Windows will rewrite the MBR thus removing GRUB out of its holy place.

But this can be solved by reading: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

---

### Post by gpw797 on 2006-02-07
Thanks, I will give the grub loader option a try tonight. I also saved a copy of grub.list it should be the same when I am all done.

---

