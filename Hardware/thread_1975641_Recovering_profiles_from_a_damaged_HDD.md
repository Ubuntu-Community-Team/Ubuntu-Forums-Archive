---
title: "Recovering profiles from a damaged HDD"
date: 2012-05-07
forum: Hardware
---

### Post by rupie on 2012-05-07
I am trying to fix a dropped HDD by running Ubuntu 11.10 on bootdisc, then accessing my old HDD which is still installed within the machine and backing-up to an external HDD. It will not give me 'permissions' to access most of the data. Is this because I am running Ubuntu from the CD, or because the HDD really is totally corrupted? 
I have managed to open and access all the files which were created in Ubuntu, before I dropped it. Anything which I had brought over from a backup when I installed Ubuntu is now inaccessible. Specifically, I'm trying to get to, and copy , my Mozilla profiles (downloaded emails, address book, etc.). So I stand to lose all the most recent emails, which I had not yet backed up. Help!

---

### Post by ahallubuntu on 2012-05-07
You may need to change permissions on the files you can't access.  Try doing it in a terminal.  Let's say are you are trying to access files in this folder but don't have permission: /media/MyHardDrive/folder1

Then in a terminal (in the live CD) type:

```
sudo chmod -R 755 /media/MyHardDrive/folder1
```

which should give you read access to all the files in folder1 and also in any folders underneath of it.

---

