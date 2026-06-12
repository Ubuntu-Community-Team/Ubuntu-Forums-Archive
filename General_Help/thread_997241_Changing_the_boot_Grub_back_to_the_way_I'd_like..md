---
title: "Changing the boot Grub back to the way I'd like."
date: 2008-11-29
forum: General Help
---

### Post by Arukas on 2008-11-29
I've started experimenting with vitalization.  I downloaded openvz, and it added an ubuntu-openvz to the boot grub.  I didn't realize it would do this.  

1)  I want my normal ubuntu to be listed first, so it will boot automatically.

2)  If I don't like openVZ, is there a speical way to uninstall it since it made changes to the boot list?

---

### Post by markharding557 on 2008-11-29
you need to edit your menu.1st file
> sudo gedit /boot/grub/menu.lst 
and rearange the entries to suit

---

### Post by jpeddicord on 2008-11-29
Check out the the [startupmanager]("apt:startupmanager") package to do GRUB modifications for you. Accessible from System > Administration > Startup Manager.

---

### Post by oldos2er on 2008-11-29
> **markharding557 said:**
> you need to edit your menu.1st file
 
and rearange the entries to suit

 Should be "gksu gedit /boot/grub/menu.lst"

---

### Post by Arukas on 2008-11-29
What's gksu?

---

### Post by drs305 on 2008-11-29
> **Arukas said:**
> What's gksu?

*gksudo* and *gksu* are the front ends to the sudo command used to open graphical apps requiring administrative privileges. Here is a link explaining it:
[graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

You can also check out the man page for most commands:
```

man gksu

```

---

### Post by 10nitro on 2008-11-29
normal su and sudo are for the command line, they ask you for your password there.  gksu and gksudo pop up a window asking you for your password.

---

### Post by Arukas on 2008-11-29
Thanks for the help, just use to using sudo.  I have t he problem fix.  thanks.

---

### Post by markharding557 on 2008-11-30
> **oldos2er said:**
> Should be "gksu gedit /boot/grub/menu.lst"

quite right,i get confused now and again because ubuntu uses sudo so often

---

