---
title: "Synaptic Package Manager help!!!"
date: 2008-09-29
forum: General Help
---

### Post by domanti on 2008-09-29
Hey. I'm a complete newbcake to Linux. I've got Hardy, and have been doing fine getting most of the things I need. I just got wine, and configured it for a few windows apps that I love. (I.E. World of Warcraft lol). Anywho, now when I try to load Synaptic Package Manager, or do a "sudo apt-get"
it get this nice little error:

E: Type '--12:16:13--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.

And it closes Synaptic Package Manager, or the sudo command doesn't work.

Can anyone tell me what I've messed up now?

---

### Post by Elfy on 2008-09-29
An error during making the file has caused a corrupt sources file.

Remove it and rerun the commands

```
sudo rm /etc/apt/sources.list.d/winehq.list
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
```

Run each command seperately

---

### Post by domanti on 2008-09-29
HAHA!! It works! Thanks a bunch!

btw: THAT WAS QUICK! Fastest forum response I've had in my life! XD

---

### Post by Elfy on 2008-09-29
welcome - can you mark thread solved please - thread tools

---

