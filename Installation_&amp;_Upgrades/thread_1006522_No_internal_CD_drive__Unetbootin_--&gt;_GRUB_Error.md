---
title: "No internal CD drive / Unetbootin --&gt; GRUB Error 13 / any ideas how to install?"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by northern lights on 2008-12-09
Oye!

The scenario is like this:
- 2004 laptop, broken optical drive, no external CD drive at hand
- ran Ubuntu and other distros flawlessly before (no hardware incompatibilities)
- since optical drive is broken (2 years minimum) always installed via Unetbootin
- old, but mostly functional XP install
- screwed up since attempting fresh Intrepid install

I've always used the NetInstall option in Unetbootin (installation GUI equivalent to Alternate CD). This time around however, I was careless and forgot to manually select "ubuntu-desktop" for installation while installing, so I ended up without a graphical interface.

I can boot into the cmd-only Interpid, but neither the packages *gdm* or *ubuntu-desktop* where found for installation. Tried to ping google.com, failed. Am assuming my shell-only intrepid's networking is also not functional.

Fair enough, I figured I'd just repeat the install. Booted into Windows, ran Unetbootin again, rebooted. Now however, I get an error from GRUB (Not the initial GRUB instance though).
I boot into a GRUB menu which yields the three common *Ubuntu* entries and an *XP* one. The *Ubuntu* entries lead to the screwed up install. I pick the XP one, which leads to another boot menu, as expected, yielding a *Windows* and a *Unetbootin* entry. I pick Unetbootin. Again there's an instance of GRUB meant to fire up the Installer. This is where I now get ```
 Booting 'Unetbootin'

 (hd0,0)
 Filesystem type is ntfs, partition type 0x7
kernel /unetbtin/ubnkern video=vesa :ywrap,mtrr vga=788 installgui

Error 13: Invalid or unsupported executable format
```

C:/unetbtin/ubnkern and C:/unetbtin/ubninit are both available under XP.

The Unetbootin grub entry looks like```
find --set-root/unetbtin/ubnkern
kernel /unetbtin/ubnkern video=vesa :ywrap,mtrr vga=788 installgui
initrd /unetbtin/ubninit
boot
```

I don't see how the bonked Intrepid install could screw with Unetbootin from the XP partition or how the above GRUB entry could be faulty as Unetbootin has always looked like it and worked.

I've attempted to fix the current Intrepid install several times as well as repeatedly tried Unetbootin (even different versions), always with the same result. I know an external CD drive would be an option, but if I had one or could easily get one other than through buying it, I wouldn't be posting.

Thanks for reading and possible input, Johannes

---

### Post by northern lights on 2008-12-10
bump

---

### Post by northern lights on 2008-12-14
bumparoo

---

