---
title: "GNU GRUB Problem"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by hl2mukkel on 2009-11-07
Hello,

Today I've just installed Ubuntu 10.9 on my PC and I'm now using a dual boot with Windows 7 and Ubuntu. Now I want to change that at the Mutliboot automaticly 'Windows 7' is selected and the timeout is 5 seconds. I've tryed to solve that problem for 2 hours but it didn't worked :-(... all I know is that I have to open either
```
/boot/grub/menu.lst
```or
```
/boot/grub/grub.conf
```And that you open the files with:
sudo gedit filename

Windows 7 has the index of 4 in my list, there are 5 items on the GNU GRUB list, and windows 7 is the last one.

Note: when I open those files, it just shows an empty text document

Regards,
Aron

---

### Post by jheaton5 on 2009-11-07
If you are using grub-legacy you want to edit /boot/grub/menu.lst.

If you are using grub2 you want to edit /etc/default/grub
After making the changes to /etc/default/grub, run update-grub2

---

### Post by hl2mukkel on 2009-11-07
> **jheaton5 said:**
> If you are using grub-legacy you want to edit /boot/grub/menu.lst.

If you are using grub2 you want to edit /etc/default/grub
After making the changes to /etc/default/grub, run update-grub2

My version from Grub is 1.96~beta4

when I type "/etc/default/grub":
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```Edited it now there, Awesome if that works :D

EDIT: Damn it doesn't work :(
I changed all the values, still wont work

---

