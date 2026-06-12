---
title: "I am in big trouble...please help"
date: 2008-10-26
forum: General Help
---

### Post by DerPhalax on 2008-10-26
I recently got linux(yesterday) and have found it to be great! but today when i booted my machine up and selected Ubuntu, instead of going to GNOME it loads for about 1 sec and then diverts to a screen saying intrinifms or something that and wants me to input commands, i have no idea what to do. Please help, if Required i will pint a screen shot or something

---

### Post by snova on 2008-10-26
A picture would be helpful.

---

### Post by DerPhalax on 2008-10-26
ok this is exactly what it looks like 

BusyBox v.1.1.3(Debian 1:1.3-5ubuntu12)Built in shell (ash)

Enter 'help' for a list of built in commands

(initramfs) help- I typed help

Built in commands
-----------------

.:alias breach cd chdir command continue echo end ecex exit export flase getops hash help let local pwd rend readonly unset wait 
[ [[ ask awk basename busybox catchmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo egrep hotname ifconfig ipkill In loadfont loadkmap Is mkdiv mkfifo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd rendlivh reset rm rmdir sed setkeycodes sn sleep sort stat sync trail tee test touch to true tty imcompact unare uniq wget yes

(initramfs)




Thats it..so what do i doo

---

### Post by damis648 on 2008-10-26
Try this: At you GRUB (boot) menu, press "e" on the Ubuntu option you normally boot. Go down to the second line and press "e" again. You should find yourself able to edit a line with "quiet" and "splash" at the end. Remove ONLY those two words. Now, press enter and then press "b". Wait until you see the busybox, and tell us the error messages that appeared right before that.

---

### Post by DerPhalax on 2008-10-26
Ok i did that and it loaded allot of stuff on the screen and stopped at the bottom saying 

BusyBox v.1.1.3(Debian 1:1.3-5ubuntu12)Built in shell (ash)

Enter 'help' for a list of built in commands

(initramfs)

---

### Post by damis648 on 2008-10-26
As I said, please post the errors that appeared right before that.

---

### Post by DerPhalax on 2008-10-26
I cant see it, it lods way to fast..mayb i have to re-install

---

### Post by damis648 on 2008-10-26
I don't need to know everything that appears before it, just tell us what is directly in the context right before the busybox. (Something like "ERROR: somethingsomething! DROPPING TO A SHELL!")

---

