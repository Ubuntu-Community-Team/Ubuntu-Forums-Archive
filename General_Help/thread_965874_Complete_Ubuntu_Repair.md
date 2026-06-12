---
title: "Complete Ubuntu Repair"
date: 2008-10-31
forum: General Help
---

### Post by Jtcgh on 2008-10-31
Hi,
I'm new(ish) to linux as a whole and have accidentally managed to cripple the OS (ubuntu 8.04):

Basically, while trying to install an application, there was an error which prevented any further update/application management process from running without an interrupting error. The only solution presented to me did something entirely unexpected and removed 90% of ubuntu itself. From gnome right down to the add/remove application function.

As a result, booting gives me a command prompt login, and very little else. So, my question: is there any way to restore all the standard parts of ubuntu?
I got halfway through installing from the disk, when I realised it wanted to partition my already doubly-partitioned hard drive (this is a dual boot windows machine, mind), in effect keeping the 'new' install separate from the old, non-functional one.
This is non-ideal, and overkill, really. I'm not too keen on the idea of having a 'dead' OS cluttering up my disk.

Any solutions to my problem? Is a reinstall from the disk the best way to go?

-Jt

---

### Post by Tictoon on 2008-10-31
Uhm I guess you could try to install it on a partition then remove the other partition with partition manager

---

### Post by CatKiller on 2008-10-31
If you still have dpkg installed, you can use a ```
sudo apt-get install ubuntu-desktop
``` to install the components of the base install.

If you're re-installing, you can either delete the existing Ubuntu partitons and install in the free space, or install in those partitions.

Edited to correct the typo that Sef pointed out.

---

### Post by nitrousoxide82 on 2008-10-31
In such a case, I'd say yes, the best way to go is reinstalling from the disk - it happened to me once, long ago, and that was just what I did. As for the partitioning, if you're using the standard install CD, when it gets to the partitioning screen you can select the "Manual" partitioning option and instruct the installer to use the already existing partitions - I would recommend that you format the partition used for the Ubuntu root directory (/), unless you have data on it that you must keep.

[Edit] The board here is fast - CatKiller's solution might just work. If it doesn't, so yes, a reinstall from disk is the way to go.

---

### Post by Sef on 2008-10-31
> If you still have dpkg installed, you can use a  	Code:
 	suudo apt-get install ubuntu-desktop 
 to install the components of the base install.

The command should be this:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

You should always update the repositories to the latest versions.  Also sudo has only one 'u'.

---

### Post by CatKiller on 2008-10-31
> **Sef said:**
> Also sudo has only one 'u'.

You're quite right, of course. A rather flaky keyboard combined with the fact that it's three in the morning to let that one through.

---

### Post by CatKiller on 2008-10-31
One other thing if you're re-installing; If you'd happened to have set up a separate partition for /home, then you could leave that intact when you install to preserve your settings and data, and then the settings wouldn't need to be re-configured for the new install.

If you didn't, then you could consider doing so this time round.

---

