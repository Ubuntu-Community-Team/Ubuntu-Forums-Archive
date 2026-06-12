---
title: "dual boot xp pro and ubuntu910 on seperate hard drive"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by kenpr on 2009-11-03
I have XP Pro installed on C and am trying to install Ubuntu 9.10 on F with Wubi 9.10. F drive is empty and formated (ntsf).
 
After running wubi and telling it to use F for the install and then rebooting, choosing ubuntu at the start screen it trys to continue the installation but stops with the error message
 
/scripts/casper-premount/20iso_scan:line 45:can't open /dev/sro: no medium found
 
I have wubi and ubuntu.iso in the same folder on drive C and ran wubi from there.
 
please help

---

### Post by sliketymo on 2009-11-03
> **kenpr said:**
> I have XP Pro installed on C and am trying to install Ubuntu 9.10 on F with Wubi 9.10. F drive is empty and formated (ntsf).
 
After running wubi and telling it to use F for the install and then rebooting, choosing ubuntu at the start screen it trys to continue the installation but stops with the error message
 
/scripts/casper-premount/20iso_scan:line 45:can't open /dev/sro: no medium found
 
I have wubi and ubuntu.iso in the same folder on drive C and ran wubi from there.
 
please help

 Wubi is used to install inside windows,to install to a seperate hard drive you will have to do a complete dual-boot install directing it to your  F drive.

---

### Post by mundo on 2009-11-05
kenpr, did you manage to install Ubuntu and XP on separate drives? I tried but lost the ability to boot into Windows as I don't think GRUB2 likes doing this!

---

