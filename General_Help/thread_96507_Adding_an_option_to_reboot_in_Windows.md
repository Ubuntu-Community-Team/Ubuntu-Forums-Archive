---
title: "Adding an option to reboot in Windows?"
date: 2005-11-29
forum: General Help
---

### Post by Kevinator on 2005-11-29
I've heard that it is possible to create a "Reboot in Windows" option. I saw a web page about how to do it, but I haven't been able to find it again.

I know there is a grub-reboot program, and I think it would be easy to write a script to search through menu.lst for the Windows entry and invoke grub-reboot with that entry number, but this approach has at least a few problems.

1) It prompts you before rebooting.

2) It requires sudo and a password.

3) It reboots abrupty, without any of the niceties one might expect, such as asking if you want to save open, modified files.

Any ideas on how to improve on this?

---

### Post by amohanty on 2005-11-29
Are you talking about this:
[http://robotics.caltech.edu/~klk/zpublic/grubbootwindows.sh](http://robotics.caltech.edu/~klk/zpublic/grubbootwindows.sh)

AM

---

