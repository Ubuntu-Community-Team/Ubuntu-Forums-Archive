---
title: "boot options (acpi=ON) overwritten?"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by melissawm on 2006-07-25
Hi, sorry if this is already a thread but i couldn't find anything like this...

My problem is this, I have an Acer Aspire 5502 and to install Dapper I had to turn off some options during instalation (the famous "acpi=off noapic nolapic" etc). So when i had everything working, i just went to the grub menu.lst, edited the boot options and - voila, acpi works just fine.

However, everytime there is a kernel update, my acpi boot options just reset to what they were during instalation - meaning "acpi=off".

This is obviously easily fixed - i just go back and edit menu.lst each time, but there must be some way to make these options default. Otherwise it is really annoying, specially because without acpi the fan doesn't work properly, it has only one speed, i can't get ubuntu to turn off etc... (hangs on "will now halt" issue.)

Can anyone help me please? ;) Thanks.

---

### Post by zgoda on 2006-07-25
Read carefully comments in /boot/grub/menu.lst - you have to change entry template (located at the end of file), not actual entry. New entries are created using these templates.

---

### Post by melissawm on 2006-07-27
I knew it must be something stupid... thanks :)

---

