---
title: "Security Update Breaks Package Manager"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by smcqueen1 on 2009-03-21
Running Intrepid. When I logged in this morning, there was a notice of a security update. After downloading and applying it, there was an error icon in the taskbar. It said "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Read error - read(5 input/output error), E:Read error - read(5 input/output error))' This usually means that your installed packages have unmet dependencies."

Executing "apt-get upgrade" in a terminal produces the following:
Reading package lists... Done
Building dependency tree       
Reading state information... Error!
E: Read error - read (5 Input/output error)
E: Read error - read (5 Input/output error)

running "dpgk --configure -a" does not help.

---

### Post by zvacet on 2009-03-21
```
sudo apt-get -f install
```

---

### Post by smcqueen1 on 2009-03-21
> sudo apt-get -f install produces the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Error!
E: Read error - read (5 Input/output error)
E: Read error - read (5 Input/output error)

---

### Post by smcqueen1 on 2009-03-22
Now I'm getting fsck errors when rebooting after the system hung. Am I just going to have to reinstall 8.10? How often does this happen? I have a server running gentoo (with kde) which hasn't been rebooted in 131 days (I just now checked uptime), while I have installed, reinstalled, and rebooted ubuntu several times in the past few days--sometimes at my instigation, other times because it just died. Is there a general instability issue with ubuntu (or maybe gnome, or ...)?

---

### Post by smcqueen1 on 2009-03-22
Of course, it could also be that my hard drive really is going bad and not really an ubuntu issue at all. We'll see.

---

