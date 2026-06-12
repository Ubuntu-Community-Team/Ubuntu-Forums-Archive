---
title: "cannot ls"
date: 2011-04-08
forum: Hardware
---

### Post by dalek-kaan on 2011-04-08
ls: error while loading shared libraries: /lib/libacl.so.1: invalid ELF header

I get this when i open the terminal in UBUNTU 10.10 
i can still type but it's just above samuel@Klaxon:~$

s: error while loading shared libraries: /lib/libacl.so.1: invalid ELF header
samuel@Klaxon:~$

this just started yesterday i've been running this computer for a couple of months with no problems 
and then suddenly that appears and the computer wont play sound 

if anyone knows what is going on i would appreciate it very much. thank you

---

### Post by Yellow Pasque on 2011-04-08
Possible file corruption. Re-install problematic package/file:
```
sudo apt-get install --reinstall libacl1
```
fsck of your / is also a good idea.

---

### Post by cjhabs on 2011-04-08
check that you are picking up the correct ls command.

```
which ls
```

---

