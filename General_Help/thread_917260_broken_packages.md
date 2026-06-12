---
title: "broken packages"
date: 2008-09-11
forum: General Help
---

### Post by xGutsAndGloryx on 2008-09-11
i am trying to install a program and it's telling me i have  some broken packages? how do i fix them?

---

### Post by kokkus on 2008-09-11
Try sudo --fix-missing
If that doesn't work, reboot, start kernel recovery mode from grub.
Choose Try to fix broken packages.
If this won't work, start your ubuntu again and open terminal, type

sudo apt-get clean 
sudo apt-get upgrade
sudo apt-get update

See if this helps you.

---

### Post by cadcrazy on 2008-09-11
Try 
> sudo apt-get install -f

This wiil surely fix the broken packages

---

