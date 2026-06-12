---
title: "Run level"
date: 2008-09-05
forum: General Help
---

### Post by sulekha on 2008-09-05
Hi,


 How to change default run level in  ubuntu 8.04 ?

 1) why there is no /etc/inittab file
 2)locate inittab is giving the result as 

/usr/lib/upstart/migrate-inittab.pl
/usr/share/vim/vim71/syntax/inittab.vim

---

### Post by iaculallad on 2008-09-05
To change your run levels in Ubuntu from tty1 (CTRL+ALT F1) you can type:

```
telinit 1
```

Or other run levels you want (0-6).

EDIT: If it helps, try reading this [page]("http://www.debian-administration.org/articles/212").

---

### Post by sulekha on 2008-09-05
> **iaculallad said:**
> To change your run levels in Ubuntu from tty1 (CTRL+ALT F1) you can type:

```
telinit 1
```

Or other run levels you want (0-6).

EDIT: If it helps, try reading this [page]("http://www.debian-administration.org/articles/212").

this is not what i want.

what i want is whenever the system boots it should boot int text mode or run level 1, for this purpose which file should i edit ?

---

### Post by fsmithred on 2008-09-05
> **sulekha said:**
> 
what i want is whenever the system boots it should boot int text mode or run level 1, for this purpose which file should i edit ?

There should be an entry for single user mode in your grub list. Edit /boot/grub/menu.lst "default num" section at the top. Change (probably) "default 0" to "default 1" and you will boot to runlevel 1 without having to select it from a list.

If you want to boot into multi-user cli, then you need to create a multi-user, non-graphical runlevel. Just turn off gdm in runlevel 2. You can use update-rc.d to do this, or you can do it manually:
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm
```
and to reverse that:
```
sudo mv /etc/rc2.d/K70gdm /etc/rc2.d/S30gdm
```

---

