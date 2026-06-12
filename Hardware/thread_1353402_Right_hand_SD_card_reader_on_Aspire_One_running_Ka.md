---
title: "Right hand SD card reader on Aspire One running Karmic."
date: 2009-12-12
forum: Hardware
---

### Post by stchman on 2009-12-12
Hello all.  I have an Acer Aspire One ZG5 and the RH SD card reader is still not hot swappable.

I used this to fix:

```

GRUB_CMDLINE_LINUX_DEFAULT=”pciehp.pciehp_force=1 elevator=noop quiet splash”
```

Added this to /etc/default/grub

When the update manager upgraded the kernel to 2.6.31-16 neither SD card reader was hot swappable.  Adding the code above made the LH reader hot swappable.

Does anyone have a fix for the RH card reader?

Thanks.

---

### Post by markbuntu on 2009-12-13
If you have a card in the righthand cardreader when you boot up you should be able to hot swap it.

---

### Post by mordalo on 2010-05-05
It doesn't, though.

I did a wipe and reinstall with 10.04 and the card reader still doesn't work.  The patch does not work.  Inserting a card and cold and warm rebooting doesn't work.

---

