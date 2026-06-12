---
title: "Upgraded from 8.10 to 9.04.  Grub menu didn't change; still tried to boot 8.10"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2009-05-23
A friend of mine just upgraded from 8.10 to 9.04... and I have a feeling that while he was doing that he told it to retain his older copy of his menu.lst file, but chances are the rest of the upgrade actually went okay.

When he tries to boot using the 8.10 option from grub, it send him strait to a single user root prompt, and that's it.

---

### Post by taurus on 2009-05-23
Look in /boot to see if there is a new kernel from jaunty.  Then, edit /boot/grub/menu.lst and include an entry for the new kernel.

```
ls -la /boot
```

---

