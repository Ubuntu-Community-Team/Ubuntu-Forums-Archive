---
title: "Grub fakeraid please help"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by mjleppan on 2009-03-07
Hi I am trying to install Linux for the first time. 

I've followed this guide...[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Its all good till I get to the point where I need to install Grub. 

point 26. "grub --no-curses" 

I get this error message:

root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

Please help me :) I want to have Linux installed!

---

### Post by Pumalite on 2009-03-07
Post:
```
sudo fdisk -lu
```

---

### Post by Pumalite on 2009-03-07
Can you boot a Live CD?

---

