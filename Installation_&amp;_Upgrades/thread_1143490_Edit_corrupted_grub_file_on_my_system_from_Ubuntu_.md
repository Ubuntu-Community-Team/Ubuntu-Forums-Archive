---
title: "Edit corrupted grub file on my system from Ubuntu 9.04 Live CD"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by wklang on 2009-04-30
My face is red.

I edited my menu.lst file in the /boot/grub directory and made a serious typo. I get a kernel panic on trying to boot.  (I saved a backup of the original (working) file before I edited the menu.lst file.)

I booted from the Ubuntu 9.04 Live CD and then navigated to the corrupted file on my machine. I can see it, open it in an editor, but cannot save the fixed file becuause I don't have root privileges (on the Live CD, I presume).

Any ideas on how I can gain editing access to my grub menu.lst file?

Thanks,

Wes

---

### Post by cariboo on 2009-04-30
Use sudo when editing and saving files using the LiveCD. You don't need a password.

---

### Post by wklang on 2009-04-30
Thank you very much for the solution, cariboo907.  I'm back in business and being a little more careful in editing this file.

---

