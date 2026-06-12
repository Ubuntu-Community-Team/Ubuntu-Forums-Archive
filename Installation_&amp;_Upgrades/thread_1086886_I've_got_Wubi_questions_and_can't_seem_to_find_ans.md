---
title: "I've got Wubi questions and can't seem to find answers in Wiki"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Zaragon on 2009-03-04
I've got a couple of Wubi questions.  
1) Does Wubi run inside Windows, outside Windows or virtual?  If inside, does it use it's own drivers or those of Windows?
2)  Does Wubi retain the vaunted integrity against malware that an install of Ubuntu has?

My thanks in advance for any knowledge you pass on to me.

Zack

---

### Post by avtolle on 2009-03-04
Wubi itself is an .exe program, and installs Ubuntu, which, once installed, runs independently of Windows (once booted up) on a virtual partition created on the HDD. As such, Ubuntu uses "its own drivers" rather than those within the Windows installation.

The malware question does not subscribed to a clear, concise answer. The Ubuntu installation, being Linux, will not *in and of itself* be subject to malware designed to affect Windows. However, malware can and will affect the Windows installation, which may well result in your not being able to boot the Ubuntu install, as Wubi, while installing, creates a new entry for Ubuntu in the Windows bootloader; thus, if one cannot boot to the Windows bootloader, one cannot access Ubuntu.

---

### Post by albandy on 2009-03-04
wubi don't run virtualized, it creates some kind of iso file in the ubuntu folder of your windows partition.

Then it's added grub to the windows bootloader, grub loads the required drivers to mount windows partition and the special iso file and boots ubuntu.

---

