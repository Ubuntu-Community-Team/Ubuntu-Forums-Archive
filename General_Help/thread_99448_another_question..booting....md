---
title: "another question..booting..."
date: 2005-12-05
forum: General Help
---

### Post by SkillZero on 2005-12-05
hi guys (again!!!!!!!!)
i dislike windows since i am using ubuntu , so i erased it with partition magic :P
now , i still have a boot loader when i start up my computer , asking me if i want to use linux or XP.

how do i remove it?

---

### Post by Rinzwind on 2005-12-05
What bootloader is it? If it's grub edit /boot/grub/menu.lst  and put #'s ('comment') in front of the lines used for windows.

Make a backup 1st tho :) and if it's working correctly after your reboot you can always delete both the backup and the lines you commented.

---

### Post by SkillZero on 2005-12-05
if it will not work at all after?
nvm
edit:
i can't write to the file (disabled in properties-Permission , i cant press it because "im not the owner")

---

### Post by filipenetto on 2005-12-05
Try to open the file with:

[INDENT][/INDENT][COLOR="Gray"]sudo gedit /boot/grub/menu.lst[/COLOR].

---

