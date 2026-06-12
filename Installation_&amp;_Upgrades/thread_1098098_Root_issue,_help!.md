---
title: "Root issue, help!"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by 220010497 on 2009-03-16
i have ubuntu and i love it but i have a program called "aMsn" and its a windows messenger client for ubuntu but i dowloaded a theme for it but it tells me to go to all the links in the file system and copy them and then i get: "you have no permission to accses or write in the file"     even thought i installed ubuntu and i am the main user, and when i try to change the file to be written in i get: "ERROR: You cannot perform this operation, only the owner: root can do this"      so i'm like ok.... so i try to logg into root and i get the pasword right but it keeps saying: "your not alowed to logging into adminastrator through this loggon platform" and all i can say is:   SON OF A MOTHER F**KING BITCH!!!


please help:

Love:220010497 aka Connan:KS

---

### Post by taurus on 2009-03-16
Even if you are the only user on your system, you are not root.  You are just a user who happens to have root privilege.  If you need to move something outside your $HOME, open a terminal and run nautilus with root privilege.

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

p.s.  And if you have a problem or question, just ask.  No need to use that kind of language.

---

### Post by Pastor_JW on 2009-03-16
[QUOTE=220010497;6906614]i have ubuntu and i love it but i have a program called "aMsn" and its a windows messenger client for ubuntu but i dowloaded a theme for it but it tells me to go to all the links in the file system and copy them and then i get: "you have no permission to accses or write in the file"     even thought i installed ubuntu and i am the main user, and when i try to change the file to be written in i get: "ERROR: You cannot perform this operation, only the owner: root can do this"      so i'm like ok.... so i try to logg into root and i get the pasword right but it keeps saying: "your not alowed to logging into adminastrator through this loggon platform" and all i can say is:  

I can understand a new user being very frustrated when first tries to do something in Ubuntu, I was too. This link will give you a way to ease your frustration.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  BTW- If you would try to tame your language a bit I would appreiciate it.  Thanks!  :)

---

