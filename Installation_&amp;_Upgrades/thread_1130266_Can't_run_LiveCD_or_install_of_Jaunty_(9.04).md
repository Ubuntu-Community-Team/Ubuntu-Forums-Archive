---
title: "Can't run LiveCD or install of Jaunty (9.04)"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Pasdar on 2009-04-19
I haven't been able to install any version of Ubuntu on my laptop, but I thought I'd give 9.04 a try, but still nothing.

This is what I see when I have AHCI enabled in bios:
```
[Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[Firmware Warn]: MTRR: CPU 1: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
ata1: softreset failed (device not ready)
ata3: softreset failed (device not ready)
modprobe: FATAL: Could not load libmodules2.6.28-11-genericmodules.dep: No such file or directory

Loading, please wait...

BusyBox v1.10.2 (Ubunu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

And this is what I see when I set it to Native IDE:
Install is no success either, with any setting enabled or disabled.

---

### Post by Pasdar on 2009-04-19
Any help appreciated... just don't tell me to try alternative cd, heh

---

