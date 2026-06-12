---
title: "[SOLVED] Shortcut to Windows"
date: 2008-10-03
forum: General Help
---

### Post by gecko3940 on 2008-10-03
In Community Documentation I found a way to shortcut to windows by double clicking a shortcut on my Ubuntu desktop.  This resets the computer and then my XP operating system loads at the grub menu. 
Here is the link (near bottom of page): [https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems](https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems).

However it involves running sudo visudo and entering the following:
ALL ALL= NOPASSWD: /usr/sbin/grub-set-default
ALL ALL= NOPASSWD: /sbin/reboot

I'm running Hardy Heron and I cannot get this part to work. So every time I use my shortcut to windows, I have to run in terminal my password, because my user account hasn't got privilege to use this shortcut.

Does anyone know how I can fix this?

---

### Post by ad_267 on 2008-10-03
Why can't you get this part to work? Is it because you don't know how to use vim? I think there is a way to make visudo use a graphical editor like gedit or a simpler editor like nano but I don't know how to do this.

Just enter in a terminal "sudo visudo" then use the down arrow keys to get to the bottom of the page then press the "i" key and you can type in those two lines at the bottom. When you're done press Esc and then ":wq" to save what you have done.

---

### Post by gecko3940 on 2008-10-04
Thanks for the quick reply, it's now working.

---

### Post by ad_267 on 2008-10-04
Just found that for future reference you can use 
```
export EDITOR=gedit && sudo -E visudo
```
to use visudo with gedit, the graphical text editor.

---

