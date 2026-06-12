---
title: "GRUB lockup"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by cimnik029 on 2005-07-16
ive tryed two linux distros, SUSE 9.3 and ubuntu, and both times iv had this problem... the installed would work fine and everything would get installed properly. when it came now to finishing the installation/rebooting, both installers would hand indefinatly. so i would press the button and reboot machine.

when it came then to booting from disk, it would display "GRUB Loading stage 1.5."
the next line would have a blinking cursor and it would freeze indefinatly. anyone got any suggestions on how to correct this?

i have windows xp proffectional installed in the first partition and ubuntu installed in the second.

my processor:     AMD 64 bit processor
my harddrive:     Maxtor DiamondMax 10 SATA (sata drivers are installed)

---

### Post by stevenyu on 2005-07-16
what happen if you try lolo?

---

### Post by cimnik029 on 2005-07-16
i tried installing that... it says, when i try installing lilo either on the master boot sector or on the linux partition, that it fails and cannot complete the task. (i checked in the installed and my cd is valid so i doubt its a problem with the cd).

---

### Post by luca_linux on 2005-07-18
Could you post your /boot/grub/menu.lst?

---

