---
title: "Dual Boot Windows 7 / Ubuntu"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by weaselnet on 2009-11-02
Thought I would post for those who might be having the same problem. The grub boot loader restore options do not work with Windows 7 build 7600. I attempted the boot to live cd options.

sudo grub
find /boot/grub/stage1
root (hd0,5)
setup (hd0,5)
quit

Windows 7 would still boot straight up ignoring the grub bootloader. So my fix was a download of EasyBcd to add Ubuntu to Windows 7 bcdedit. You may download a copy at [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1).

weaselnet

---

