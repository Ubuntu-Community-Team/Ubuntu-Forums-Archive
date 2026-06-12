---
title: "Can't use Sudo anymore"
date: 2008-09-28
forum: General Help
---

### Post by josephellengar on 2008-09-28
Help me!  Whenever I try to use the sudo command I get an error that says, "must be setuid root."  When I try to do setuid root i get:
The program 'setuid' is currently not installed.  You can install it by typing:
sudo apt-get install super
bash: setuid: command not found

And when I try to install setuid I get must be setuid root.  What can I do about this?  Is there anything that I can do with a live disk to fix this?  I think that I might have changed ownership on my /usr or /usr/bin directories, if that helps at all.  Any help would be greatly appreciated.

---

### Post by iaculallad on 2008-09-28
In your terminal:

```
sudo chown root:root /usr/bin/sudo
sudo chmod 4755 /usr/bin/sudo
```

Then try logging out from your account and log back in.

---

### Post by kokkus on 2008-09-28
Do you get the same errors when you login in terminal session and not in gnome? If not, try sudo apt-get install super. If yes, reboot, open shell command in recovery mode and type sudo --fix-missing or in recovery mode, try to repair broken packages.
Neither works? Start shell command again and type
sudo chown root:root /usr/bin/sudo && sudo chmod 4755 /usr/bin/sudo

---

### Post by josephellengar on 2008-09-29
Thanks much both of you.  That worked perfectly!

---

