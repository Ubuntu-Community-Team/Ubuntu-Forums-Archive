---
title: "Error starting volume group: Authentication is required"
date: 2011-07-16
forum: Hardware
---

### Post by r0t on 2011-07-16
Hello, since upgrading to 11.04 I can no longer access one of my hard drives. It has a volume group with two volumes, which I can see in Disk Utility (2.32.1). Trying to start them from there gives ”Error starting volume group: Authentication is required”, and trying to mount them in Gnome gives ”Failed activating drive: Authentication is required”.

Something might have gone bad during upgrade as I had to redo the upgrade several times (before I finally got Gnome working with my Graphic Card. Still no success with Unity :-/ ). During the way I this the users got erased, because during the last, and successful, attempt I was asked to enter my user info again. Any suggestions how to troubleshoot this?

GParted does not seem to recognize the partitions at all, btw, just says ”unallocated” there.

---

### Post by r0t on 2011-07-23
*bump*

---

### Post by r0t on 2011-08-02
I now tried Palimpsest, which, run as root, gives me a new error message when trying to start the volume: ”Failed to execute child process "lvchange" (No such file or directory)”. Does this make sense to somebody?

---

### Post by r0t on 2011-08-02
For anyone else with this problem: Through another forum I found out that the program lvm2 was removed during upgrade to 11.04. Running ```
sudo apt-get install lvm2
``` solved the problem.

---

### Post by russian460 on 2012-02-24
Thanks bro, but I also has to 

sudo apt-get install cryptsetup

---

