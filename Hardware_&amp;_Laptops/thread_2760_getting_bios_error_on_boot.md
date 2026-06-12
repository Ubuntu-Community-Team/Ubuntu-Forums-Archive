---
title: "getting bios error on boot"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by Arbiter on 2004-10-31
Hi everyone,

I just switched my Sony FXA-32 laptop over from Fedora Core 2 to Ubuntu, and I must say that Ubuntu is far superior, but I digress...

I'm getting an error on boot that says that my bios has caused a fatal error and I should add "nobiospnp" or something like that to my grub boot file.  The machine boots without error after receiving this message and nothing else goes wrong (that I can see, at least).  It says something about upgrading my laptop's bios, but I don't want to have to do that.

Any help would be greatly appreciated!  :D

---

### Post by taygan on 2004-10-31
If it says to update your BIOS that really should be done..  Things will work much better.  to disable your pnpbois try this from Applications-system tools-terminal:
[I]
sudo nano /boot/grub/menu.lst[/I]

then edit the lines that start with "kernel" they should say something like

title ............
root .............
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash [COLOR=Red]pnpbios=off[/COLOR]

you add the pnpbios=off part

ctrl-x to exit, Y to save, enter to save it as the same file you opened

---

### Post by nightmaresc on 2004-10-31
[QUOTE=taygan]title ............
root .............
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash [COLOR=Red]pnpbios=off[/COLOR]

you add the pnpbios=off part[/QUOTE]

I have the same problem.

The error message doesn't go away for me by adding that.

---

### Post by Arbiter on 2004-10-31
The pnpbios=off thing worked for me.  Still working out some other problems though.

---

### Post by nightmaresc on 2004-11-02
Sorry!

I entered the wrong command.  I was getting so used to typing 'nobiospnp' that I put nobiospnp=off instead of the right command.

It fixed the error, thanks.

---

