---
title: "manual file system checking"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by arunkumar413 on 2009-01-17
/dev/sda7 contains a file system with errors,check forced.
/dev/sda7.
inodes that were part of a corrupted orphan linked list found.
/dev/sda7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.(i.e., without -a or -p options)
fsck died with exit status 4.

*an automatic file system check (fsck) of the root file system failed.
a manual fsck must be performed,then the system restarted.The fsck should be performed in maintenance mode with the root file system mounted in read only mode.

*the root file sytem is currently mounted in read only mode.

A maintenance shell will.........
This is the message i get when i try to boot ubuntu 8.10.It is asking for a root password for manual file system check.I forgot the root password.am unable to boot linux.please help me

---

### Post by Tim Sharitt on 2009-01-17
Have you set a root password?

---

### Post by arunkumar413 on 2009-01-17
no

---

### Post by Tim Sharitt on 2009-01-17
You can run fsck off of a live cd. Open a terminal and run:
```
sudo fsck /dev/sda7
```

---

### Post by arunkumar413 on 2009-01-17
> **Tim Sharitt said:**
> You can run fsck off of a live cd. Open a terminal and run:
```
sudo fsck /dev/sda7
```
does this work even if i have two linux OS.i have ubuntu8.10 and BOSS Linux.

---

### Post by Tim Sharitt on 2009-01-17
Yes, you should be able to use it from any linux distribution for any linux file system.

---

### Post by Archmage on 2009-01-17
Most of the time the root-password is the password of the first user.

---

