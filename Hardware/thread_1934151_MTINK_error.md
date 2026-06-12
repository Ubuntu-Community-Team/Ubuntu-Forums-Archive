---
title: "MTINK error"
date: 2012-03-01
forum: Hardware
---

### Post by MrCorleone87 on 2012-03-01
Hey guys,

I've just installed Mtink program to display the ink levels in my Epson Stylus SX210 printer but when I launch the software I get the following error message: 

,,No access to printer device file. Please make sure that Mtink has enough right for accessing the device files.

On Debian based system as Ubuntu you must be a member of the group lp."

What does all that mean?  What should I do?

Thanks in advance for any replies!

---

### Post by ajgreeny on 2012-03-01
Add your user to the group lp, as the error message says.  Go to "Users and groups" to make the change, or you can do it in terminal, or even by editing the file /etc/group to add your user so it looks like this, which is the top part of mine, though some details may, of course be different
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:*username*
tty:x:5:
disk:x:6:
[COLOR=Red]lp:x:7:*username*[/COLOR]
mail:x:8:
news:x:9:
```Knowing mtink, it may take a few minutes the first time you try it, even after adding your user to that lp group, but it should work.  You may even need to reboot before the system picks up the change.

---

### Post by MrCorleone87 on 2012-03-02
Nice one mate, worked perfectly! Cheers!

---

