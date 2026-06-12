---
title: "Booting into Vista by default"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by eyescovered on 2009-04-28
hey all. i recently installed Ubuntu 9.04 along side Vista. when i turn on the computer, the default OS that's highlighted is Ubuntu. I want it to be Vista until i get Ubuntu the way i like it. is there a way to change the order?

 i tried searching for this, but didn't see anything. thanks in advance!

---

### Post by alphacrucis2 on 2009-04-28
> **eyescovered said:**
> hey all. i recently installed Ubuntu 9.04 along side Vista. when i turn on the computer, the default OS that's highlighted is Ubuntu. I want it to be Vista until i get Ubuntu the way i like it. is there a way to change the order?

 i tried searching for this, but didn't see anything. thanks in advance!

See item 10.

[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

---

### Post by b@sh_n3rd on 2009-04-28
You can. I haven't done it for windows "Vista" though. But there shouldn't be a difference. Only difference there would be is the name of the OS on the GRUB bootloader file. Type: ```
sudo gedit /boot/grub/menu.lst
``` in a terminal. Then find a statement that says something like; "title    windows xxxxxx". Under that, see if you could find something like "default x". "X" is a number, Change it to the order you prefer. (eg: ubuntu would be 1 and vista 0) The problem is I haven't done this in a while and I can't remember how I did it. If you run into problem's show me your "menu.lst" file and I will remember in a jiffy! :D hope this helps.

**EDIT:** The above linked site is quicker, its the same as I mentioned but is graphical, so it's easier to follow.

---

### Post by alphacrucis2 on 2009-04-28
> **b@sh_n3rd said:**
> You can. I haven't done it for windows "Vista" though. But there shouldn't be a difference. Only difference there would be is the name of the OS on the GRUB bootloader file. Type: ```
sudo gedit /boot/grub/menu.lst
``` in a terminal. Then find a statement that says something like; "title    windows xxxxxx". Under that, see if you could find something like "Default x". (this is not the "default" located at the top of the file). The problem is I haven't done this in a while and I can't remember how I did it. If you run into problem's show me your "menu.lst" file and I will remember in a jiffy! :D hope this helps.

Just a note. I'm told you aren't supposed to run gnome programs like gedit using sudo to get admin rights. The recommended way to do it is:

 ```
gksu gedit ...
```

---

### Post by pokogr on 2009-04-28
In order to avoid terminal you may install a useful application called startupmanager from synaptics package manager. Then use this application to select the os you want to be the default on each boot.

---

### Post by dLeon on 2009-04-28
Check/edit your /boot/grub/menu.lst as root (use sudo). I will not into details because the menu.lst filled with comments to do what you want. If still not clear, read 'grub man page'. Still not clear, come back here.

Warning: Please becareful when editing your grub menu.lst. Don't touch anything that look cryptic for you.

---

### Post by b@sh_n3rd on 2009-04-28
> Just a note. I'm told you aren't supposed to run gnome programs like gedit using sudo to get admin rights. The recommended way to do it is: "gksu gedit ..." Hey, coo. Thanks for that. I'll recompile my "ubuntu_command_list" under my cranium. ;)

---

### Post by eyescovered on 2009-04-28
wow. thanks for the fast responses!!! got it working! thanks for the all the help!

---

