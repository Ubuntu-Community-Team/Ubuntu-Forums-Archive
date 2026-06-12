---
title: "shortcut list for operating system"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by faisalloe on 2005-09-11
i m new user of ubuntu
mouse not working  ](*,) 
any one knows shortcuts list ?

---

### Post by krusbjorn on 2005-09-11
If your mouse is not working, try reconfiguring your xorg package.

Open a terminal (alt+F2, type "gnome-terminal", hit enter) and, in the terminal type "sudo dpkg-reconfigure xserver-xorg". You'll be asked to fill in some stuff about your keyboard, mouse, video card etc...

When done, restart X by pressing ctrl-alt-backspace, and see if it works :)

---

### Post by faisalloe on 2005-09-11
othanx.
let me check it.

---

### Post by faisalloe on 2005-09-11
mm and how to configure dialup internet

and...
sound
?

---

### Post by faisalloe on 2005-09-11
no i check that,mouse wont work  [-X

---

### Post by faisalloe on 2005-09-11
[QUOTE=faisalloe]no i check that,mouse wont work  [-X[/QUOTE]
 i tried this

If your mouse is not working, try reconfiguring your xorg package.

Open a terminal (alt+F2, type "gnome-terminal", hit enter) and, in the terminal type "sudo dpkg-reconfigure xserver-xorg". You'll be asked to fill in some stuff about your keyboard, mouse, video card etc...

When done, restart X by pressing ctrl-alt-backspace, and see if it works 



but its not working :(
what should i do now.

---

### Post by mlomker on 2005-09-11
[QUOTE=faisalloe]but its not working :(
what should i do now.[/QUOTE]

Let's see if the kernel is recognizing the mouse.  Try this in a terminal: **dmesg | grep mouse**

---

### Post by faisalloe on 2005-10-30
oki guys let me check it first then i let u know guys about it.

---

