---
title: "[SOLVED] force password entry for Grub entry"
date: 2008-08-25
forum: General Help
---

### Post by slvjerome on 2008-08-25
I've got Hardy Heron installed and am setting it up for a Kiosk application.

On startup, when the user hits ESC to enter the Grub menu, I'd like to force the user to enter a password.  

If that isn't possible, then I'd like it if the user must enter a password to select a non-default entry from the grub menu.

I've installed StartUp-Manager and in the Security tab I've checked all 3 Protection Options.  But the user can still select a non-default entry (e.g. Recovery Mode).

Thanks!
Jerome

---

### Post by Elfy on 2008-08-25
You can lock different stanzas in the menu list it appears, I think this uses the password you have set with sum - but I prefer to edit mine by hand so can't be completely sure.

Open the menu as root to edit it

```
gksudo gedit /boot/grub/menu.lst
```

Under the title of the option you need to lock - ie recovery modes you need to put lock

> title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
[COLOR="Blue"]lock[/COLOR]
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic 

This is the grub manual document page, there is quite abit in here on security

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by lackoblacko on 2008-08-25
this tutorial will tell you how to secure your grub menu

[http://ubuntuforums.org/showthread.php?t=715630&highlight=grub](http://ubuntuforums.org/showthread.php?t=715630&highlight=grub)

just add the lock command to each entry in order to require a password.

---

### Post by slvjerome on 2008-08-25
> **forestpixie said:**
> You can lock different stanzas in the menu list it appears, I think this uses the password you have set with sum - but I prefer to edit mine by hand so can't be completely sure.

Open the menu as root to edit it

```
gksudo gedit /boot/grub/menu.lst
```

Under the title of the option you need to lock - ie recovery modes you need to put lock



This is the grub manual document page, there is quite abit in here on security

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

Worked perfectly.  Thanks!

---

### Post by Elfy on 2008-08-25
Glad I could help, perhaps you could mark thread solved next time you are here, if you see the post of course.

---

