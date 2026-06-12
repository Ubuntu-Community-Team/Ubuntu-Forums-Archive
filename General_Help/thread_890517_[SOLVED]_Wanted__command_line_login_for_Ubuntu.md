---
title: "[SOLVED] Wanted: : command line login for Ubuntu"
date: 2008-08-15
forum: General Help
---

### Post by rated727 on 2008-08-15
for reasons that aren't worth recounting here, I want to eliminate all of the "pretty" until Ubuntu/Gnome actually starts.

I have already dumped the graphic Logo Screen/Progress Bar

-- in /boot/grub/menu.lst - change from;
kernel   /boot/vmlinux-2.6.24-19-generic root=(....) ro quiet splash
-- to the following;
kernel   /boot/vmlinux-2.6.24-19-generic root=(....) ro verbose vga=791

'verbose' needs no explaination - VGA=791 sets the text screen at 1024X768 resolution

Then, it opens to the graphic login screen.  I prefer to have it stay in text mode and issue a simple "login" prompt.

I've tried various options in the [System] - [Administration] - [Login Window Preferences] with no success (and one massive failure that required reinstallation)

How do I entirely eliminate the graphic login screen?

---

### Post by rated727 on 2008-08-15
Refining the request above:

Somewhere there is a script or config file that calls to load GDM and thus, the graphic login screen.  This file would have to be changed when one selects a different login theme ... so I would like for my login theme to be supplied by a text based script.

Does anyone know what and or where?

... once that script or config file is located, does anyone have a clue about how to call up a BASH script to handle the login (I should be able to write that for myself) then pass control over to Metricity, Compiz or another desktop manager?

---

### Post by Genius314 on 2008-08-15
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I think that topic might have the information you need. :)

EDIT: Yeah, you have to follow the instructions, then disable GDM from the list of startup processes. That should do it, although I don't know for sure, since I didn't try it myself.

I don't know how to login from the command line, though.

---

### Post by Locutus_of_Borg on 2008-08-16
i think you can just append 'init=/bin/bb' to your kernel line, then just issue startx after you login

---

### Post by rated727 on 2008-08-16
[SIZE="3"]**THANK YOU!**[/SIZE]

your offering was clearly a step in the right direction.  But, the system complained that "the target file system doesn't have /bin/bb. (eventually it brought up Debian's limited "BudyBox" shell)

I changed it to read [FONT="Arial"][SIZE="2"]init=/bin/bash[/SIZE][/FONT] and got to a BASH shell, but without privileges to run startx.

[SIZE="3"]**But this is very definitely the first step in the right direction!!**[/SIZE]

At least now, I have the means to launch the BASH shell rather than the graphic Gnome login.  I can surely build the (BASH) login script then drop through an automatic (uncontested) login to X (Gnome/Ubuntu)

---

### Post by spupy on 2008-08-17
The link that **Genius314** posted contains the solution. GDM is much like a service that runs at boot - but it runs at the very end. Just disable it.

---

### Post by 982000971 on 2009-11-21
Thanks!

---

