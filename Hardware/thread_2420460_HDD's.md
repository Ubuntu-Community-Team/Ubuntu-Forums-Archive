---
title: "HDD's"
date: 2019-06-06
forum: Hardware
---

### Post by iulian212 on 2019-06-06
So the thing is that i have a SSD(120GB) on which i installed ubuntu and i have two other HDD's (1.5TB and 500GB) what do i need to do so i can install apps on them too especially steam games since the sdd is very small in size

---

### Post by drv9977 on 2019-06-06
Ubuntu by default uses it own directory for application installation also. Although some third party applications may ask you to set installation directory.

---

### Post by CatKiller on 2019-06-06
The simplest way is to mount one of those drives as /home. There are a bunch of tutorials for creating the partition, copying the stuff across, and then automatically mounting it at boot. All your personal files and settings, including your Steam games, are stored in your Home folder. It has the additional benefit that if you have to reinstall the OS, for some reason, you can keep all your files and settings.

---

