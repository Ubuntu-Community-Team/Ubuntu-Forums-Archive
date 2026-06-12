---
title: "Running out of room"
date: 2008-08-29
forum: General Help
---

### Post by skirby on 2008-08-29
I am running Ubuntu 804 Server on a VMWare Client running on Windows.  The VM was sized at 8GB.  Then I began to run out of room, so to increase the VM I used the vdiskManager to increase the VM to 20GB.  All well and good so far, but the Ubuntu Server still seems to think it's size is only 8GB. What do I need to change to get Ubuntu to recognize the expanded size of 20GB?

---

### Post by maybeway36 on 2008-08-29
Run the Ubuntu live CD, SystemRescueCD, or GParted Live on the virtual machine. Go to GParted, move the swap partition all the way to the right, then resize the ext3 partition to fill the free space.

---

