---
title: "[SOLVED] editing menu.1st"
date: 2008-09-15
forum: General Help
---

### Post by Samrat Rao on 2008-09-15
Hello,
    I had installed ubuntu 7.10 and more recently, openSUSE 11. So openSUSE's menu.1st comes now which redirects me to ubuntu's ment.1st. I wish to keep suse's menu.1st as the first option, but i also want to edit ubuntu's menu.1st so that i can go back to suse from there. I tried putting this entry, but i get an error message that menu.1st not found. How do i solve the problem?

title		openSUSE 11.0 - 2.6.25.5-1.1
root		(hd0,4)
configfile	/boot/grub/menu.1st

---

### Post by damis648 on 2008-09-15
Note, the file is called menu.lst, not menu.1st. (that is L)

Back up the original first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
and then edit it:
```
sudo nano /boot/grub/menu.lst
``` and change the parameters of the Ubuntu boot option to the parameters listed in the kernel version of the other (Ubuntu's) menu.lst.

---

### Post by Idefix82 on 2008-09-15
You probably mean menu.**l**st i.e. replace the number 1 with the letter l.

---

### Post by kokkus on 2008-09-15
You can also change this file if you download and run startup manager. 
Much safer if you do someththing wrong.

---

### Post by Samrat Rao on 2008-09-17
ya, i mistook the name as menu.1st instead of menu.lst . Now my problem is solved. Thanks.

---

