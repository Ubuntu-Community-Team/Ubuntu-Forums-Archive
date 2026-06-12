---
title: "Completed Installation Bootloader Broken"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by skorea2131 on 2009-02-07
Help!!! I just finished my installation on a seperate harddrive... I took my cd out of the disk and now it says an error message...somthing like "no timer detected please reboot in 'noapic' option" I can't find the option... The same thing happened when I loaded the live cd... HELP!!!

---

### Post by avtolle on 2009-02-07
Take a look at [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for how to use boot options. You need to add noapic at the kernel line in Grub (if booting from your installed system) or where indicated when booting from the Live CD.

---

### Post by skorea2131 on 2009-02-09
Thanks it helped!!!!!

---

