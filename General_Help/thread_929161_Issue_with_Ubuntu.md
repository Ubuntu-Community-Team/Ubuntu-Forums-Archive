---
title: "Issue with Ubuntu"
date: 2008-09-24
forum: General Help
---

### Post by risknothin on 2008-09-24
3 issues w/ ununtu

1. All my bookmarks in firefox are gone.

2. updates wont install - errors occur for example - see image below for erro

3. every time i reboot a routine file check attempts to run
while running i get this error around 6%
-----------------

inodes that were part of a corrupted orphan linked list found

unexpected inconsistency; run fsck manually

fsk dies with exit status 4

an automatic file system check of root filesystem failed

bash: no job control in this shell
bash: groups: command not found
bash: lesspip: command not found
bash: command: command not found
bash: the: command not found
bash: dircolors: command not found
bash: command: command not found
bash: the: command not found

--------------------
anyone know how to fix any of these issues? or all three? :)

---

### Post by tuxxy on 2008-09-24
You need to manually run a file system check as it advises you, when Ubuntu boots at the GRUB screen you press delete, now you will have some options, select recovery mode.

When you get to a prompt you run this command,

```
fsck 
```

Another method would be to enter ths command, it should fsck as it reboots

```
sudo touch /forcefsck && sudo reboot
```

---

### Post by risknothin on 2008-09-24
wow that took forever to run

the issues w/ my updates are fine but firefox still does not have any bookmarks and i cannot reload pages. the reload icon is gray

edit

forward and back icons dont work and my home page does not load

i tried uninstalling and reinstalling firefox

is there a way to remove everything and start from scratch? because apparently all the settings and suck remain even if you uninstall.

---

