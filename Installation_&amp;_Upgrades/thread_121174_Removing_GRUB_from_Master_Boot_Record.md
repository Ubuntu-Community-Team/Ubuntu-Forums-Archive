---
title: "Removing GRUB from Master Boot Record"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by crsd36 on 2006-01-24
I am a new Ubuntu user trying to install Linux onto my external hd in the method described by DaBruGo and I screwed up, and put the GRUB on the wrong drive--where my XP is installed.  Im pretty sure that i'll get an error 21 if I exit the installation.  I went back and changed the directory but I know that I'll get the 21.  Is there anything I can do?  Or will I have to reinstall Windows?  Thanks!

---

### Post by manicka on 2006-01-24
You can restore the windows mbr by booting from your windows xp disc and going into rescue mode, then running the command  - fixmbr

---

### Post by crsd36 on 2006-01-24
thanks!

---

