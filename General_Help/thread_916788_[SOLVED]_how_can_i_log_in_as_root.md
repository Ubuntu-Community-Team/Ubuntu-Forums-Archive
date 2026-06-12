---
title: "[SOLVED] how can i log in as root"
date: 2008-09-11
forum: General Help
---

### Post by x_error on 2008-09-11
hi  i want to ask you how can i log in as root or administrator with the default settings

---

### Post by eentonig on 2008-09-11
with the default settings, you can't.

You can however gain root privileges by using "sudo" in front of your commands.

> sudo command

or use 
> man sudo
to get some background info regarding it's usage.

---

### Post by Nepherte on 2008-09-11
On Ubuntu, logging in as root is disabled by default. The question is "why would you want to login as root?". If you need root privileges, just add sudo in front of the command in a console, or, if it's a graphical application, gksu(do). The forum policy requires not to inform you how to enable root login: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by gvartser on 2008-09-11
Check this out:

[http://www.sizlopedia.com/2008/04/16/how-to-login-to-ubuntu-as-root-user/](http://www.sizlopedia.com/2008/04/16/how-to-login-to-ubuntu-as-root-user/)

Its everyones right to know how to do stuff to its own belongings even if others thinks its wrong..

---

### Post by gvartser on 2008-09-11
> **Nepherte said:**
> On Ubuntu, logging in as root is disabled by default. The question is "why would you want to login as root?". If you need root privileges, just add sudo in front of the command in a console, or, if it's a graphical application, gksu(do). The forum policy requires not to inform you how to enable root login: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

He asked how he could log on as root, not become root.

/g

---

### Post by x_error on 2008-09-11
the fact that i want to login as root is because i installed a gtk 2 theme that caused ubuntu to freeze at startup and cpu sound became like a jet engine and i tried failsafe gnome but the same happens !! so what should i do !! i installed too many programs and packages and if i reinstall ubuntu they are all gone !!

---

### Post by Archmage on 2008-09-11
How about only removing the gtk-theme?

---

### Post by Nepherte on 2008-09-11
> **gvartser said:**
> He asked how he could log on as root, not become root.

/g
And?

---

### Post by Nepherte on 2008-09-11
> **x_error said:**
> the fact that i want to login as root is because i installed a gtk 2 theme that caused ubuntu to freeze at startup and cpu sound became like a jet engine and i tried failsafe gnome but the same happens !! so what should i do !! i installed too many programs and packages and if i reinstall ubuntu they are all gone !!
Open up a virtual terminal (ctrl + alt + F1) and login with your regular user. 

The themes reside in ~/.themes and /usr/share/themes. So navigate to these directories:
```
cd ~/.themes
```
or
```
cd /usr/share/themes
```

Delete the theme that's causing problems:
```
sudo rm -r "themename"
```

Switch back to graphical login with ctrl + alt + F7 and login as you normally would.

---

### Post by aysiu on 2008-09-11
Reboot into recovery mode (check out the first half of [this page](http://www.psychocats.net/ubuntu/resetpassword) if you don't know how to do that).

Then type ```
cd /home/*username*
``` where *username* is the user who freezes up and then ```
mv .themes .themes.broken
exit
``` and resume the normal boot.

---

### Post by x_error on 2008-09-11
thanks for both of you i really owe you my life ( 3 days trying to solve the problem ) but how can i know more about commands they worked but i dont know what mv .themes .themes.broken is so were can i know more about commands ? like delete copy move and other system commands that might be useful

---

### Post by aysiu on 2008-09-11
I'll explain the commands I gave you.

*cd* means *change directory*

So you changed to the home directory of your user.

*mv* means *move*. It also can, as in this case, be used to rename files and folders.

So you renamed your .themes folder to .themes.broken. So the corrupt GTK theme you installed is no longer active, and a new .themes folder will be automatically generated when you log in.

*exit* takes you out of the command line

You can learn more about commands here:
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by Nepherte on 2008-09-11
It is always a good idea to check the commands you use (or commands that other people suggest you should execute). That way you will learn them as you use them and it prevents you from using dangerous commands as well. To see what a command does, you can look at its manual by doing:
```
man command
```

---

### Post by x_error on 2008-09-11
thanks guys for all the help u gave me

---

### Post by bodhi.zazen on 2008-09-11
Best way to learn the command line is to use the command line. although cryptic at first, the command line is quite powerful, and well, addicting.

Start here : [http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

Take care, the rabbit hole is deep.

---

