---
title: "[SOLVED] HOW TO: uninstall grub??"
date: 2008-07-13
forum: General Help
---

### Post by RMD94 on 2008-07-13
Hello,

I deleted Ubuntu partition from my PC cuz my dad doesn't like Ubuntu but the problem is GRUB didn't get uninstalled so whenever i boot my PC i get an error: error 71 and i can't boot into Windows. could someone help me to how to uninstall GRUB??

plz help me!!

- Thank You

---

### Post by Rocket2DMn on 2008-07-13
If you are using XP, reboot from the install CD and enter the recovery mode.  Run
```
fixmbr
```
If you are using vista, see here - [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) - I believe you want the /FixBoot and /FixMbr commands.

---

### Post by da chicken on 2008-07-13
1. Boot from the Windows CD
   2. Select R for Recovery Console
   3. Type the number of your Windows install (usually 1) and hit enter
   4. Type in the administrator password
   5. Type fixmbr and hit enter
   6. Answer yes when it asks you to overwrite the MBR
   7. Type exit, which will then reboot the system and everything should work

---

### Post by RMD94 on 2008-07-13
I have Windows Vista.

---

### Post by Rocket2DMn on 2008-07-13
See post #2, there is a link there for exactly what you need.

---

### Post by RMD94 on 2008-07-13
It worked..

Thank You very much

---

