---
title: "Error 15"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by willyDK on 2007-08-21
An Ubuntu installation crashed and now I get the error:
Grub loading stage 1.5
Grub loading, please wait
Error 15

The computer freeze and I cant boot from the cd whatever it is a MSWindows, Debian or Ubuntu.
What can I do to resolve this problem?

---

### Post by LuckyDevil on 2007-08-21
Can you post your entires from /boot/grub/menu.lst?

Also, what does fdisk -l show?

You're just not pointing to the correct partition is what it sounds like...definitely repairable with grub commands.

---

### Post by willyDK on 2007-08-21
Hi LuckyDevil

The problem is, that I can’t do any thing.
When then computer boot up whit or without a Ubuntu, Debian or Windows cd, the computer halt in this step and came no longer.

---

### Post by LuckyDevil on 2007-08-21
Has your boot priority changed in your BIOS?  Do you have multiple drives?  If so, changing that order would cause this error.

Put the cd before the hard drives in your bios boot menu and you'll boot to the live cd.

---

### Post by milosz.galazka on 2007-08-21
Is first boot from cd set in your bios configuration?

---

### Post by willyDK on 2007-08-21
Yes. The first boot dev in bios is cd

---

