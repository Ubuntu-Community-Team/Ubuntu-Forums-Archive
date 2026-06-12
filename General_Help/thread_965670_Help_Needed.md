---
title: "Help Needed"
date: 2008-10-31
forum: General Help
---

### Post by Fez98 on 2008-10-31
Ok, i am a complete novice to Linux, let alone Ubuntu. My version is "Hardy". I just installed it, and when i try to go to the synaptic Package manager, i get 2 error messages,

1st 1. E: dpkg was interrupted and i must manually run it.

2. E: _cache -> open failed ()

I am trying to install ndis wrapper, so i can get my wifi adapter working on my computer. I am sending this from another computer.

SYSTEM SPECS (if Needed)
AMD Athlon 64 2800+
1.5GB RAM
Radeon HD 3650 Video Card

---

### Post by Fixman on 2008-10-31
> **Fez98 said:**
> Ok, i am a complete novice to Linux, let alone Ubuntu. My version is "Hardy". I just installed it, and when i try to go to the synaptic Package manager, i get 2 error messages,

1st 1. E: dpkg was interrupted and i must manually run it.

2. E: _cache -> open failed ()

I am trying to install ndis wrapper, so i can get my wifi adapter working on my computer. I am sending this from another computer.

SYSTEM SPECS (if Needed)
AMD Athlon 64 2800+
1.5GB RAM
Radeon HD 3650 Video Card

Go to Application->Accesories->Terminal, and there type

```
 sudo dpkg-reconfigure -a 
```

---

### Post by Fez98 on 2008-10-31
2nd problem, every version of NDIS Wrapper i download says either wrong architecture or Dependency not satisfiable. GNOME ver. 2.2

---

### Post by Fixman on 2008-10-31
> **Fez98 said:**
> 2nd problem, every version of NDIS Wrapper i download says either wrong architecture or Dependency not satisfiable. GNOME ver. 2.2

Do not download ndiswrapper from the internet, just open the terminal and write

```
 sudo aptitude install ndiswrapper 
```

---

### Post by Fez98 on 2008-10-31
Thanks alot man, you are a big help on getting me to learn how to run Ubuntu.

---

