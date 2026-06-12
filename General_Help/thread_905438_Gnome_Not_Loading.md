---
title: "Gnome Not Loading"
date: 2008-08-30
forum: General Help
---

### Post by fjgaude on 2008-08-30
After the last kernel update two or three days ago, my system doesn't load gnome after the login screen. I have to use the Failsafe Gnome option and then all works correctly.

What to do? The login scripts are likely in error. Where are these scripts?

Any suggestions? Thanks!

---

### Post by EmanresuusernamE on 2008-08-30
Have you tried booting into safe mode Ubuntu (not the Gnome failsafe) and then having it repair your X settings?

---

### Post by fjgaude on 2008-08-30
Yes, I'm in safe mode now... but I've rebooted into normal gnome and it's a no-go. I have used the safe mode in Ubuntu to re-boot without success.

I've tried to run **sudo gnome-panel** while in the gnome safe mode but get an error msg regarding login scripts, GTK, etc.

Where are such login scripts located?

---

### Post by TekNullOG on 2008-09-09
Have you had any luck with this? I am experiencing the EXACT same problem on my ex-gf's computer and I would like to solve this ASAP.

Damn I hate those computer calls...

---

### Post by TekNullOG on 2008-09-09
I tried selecting GNOME from the list of session instead of the failsafe GNOME and it worked. It asked me if I wanted to make it default ( i said yes ) and when I rebooted, it continued to work.

I don't know why it was no longer default after doing updates. Hope this helps others.

---

### Post by EmanresuusernamE on 2008-09-11
The failsafe version should not be your default.  Do you have a bootloader installed on your system?  If not, could you look under System > Administrator and then open Hardware Drivers.  Are you using the free, or the manufacturer's drivers?  Try toggling it.

Also, could you post the contents of your /etc/X11/xorg.conf file?

---

