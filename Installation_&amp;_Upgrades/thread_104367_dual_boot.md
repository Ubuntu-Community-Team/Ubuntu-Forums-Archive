---
title: "dual boot"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by markcaetano@gmail.com on 2005-12-16
how can i make ubuntu 5.10 dual boot with windows 98 SE with the grub loader
ubuntu is already installed and i dont want to uninstall it again cos it took me forever to get it to let alone install the damn thing

i have a 10 gb hdd and a 250 mb swap file space
all my programs are windows(shame on me) and im too confused with emulators for it to be of any use to me

P.S do u know any good free emulators

mark:confused:

---

### Post by aysiu on 2005-12-16
Ubuntu should have already added Windows to the boot menu.
Can you post the output of these two commands? ```
cat /boot/grub/menu.lst
sudo fdisk -l
```

Also, Wine is the "emulator" program you're looking for to run Windows applications. First link of my sig, then ```
sudo apt-get update
sudo apt-get install wine
``` Double-click the .exe you want to run.

---

### Post by markcaetano@gmail.com on 2006-01-31
ok i got the dual boot workinw with win98 but it dosent show up on grub
CAN ANYONE HELP ME WITHIN IN THE NEXT 24 HOURS BECAUSE SCHOOL STARTS TOMORROW AND I NEED MY WINDOWS FILES AND PROGRAMS FOR SCHOOL !!!

---

### Post by aysiu on 2006-01-31
Did you read my post--the one reply to your first message?

---

