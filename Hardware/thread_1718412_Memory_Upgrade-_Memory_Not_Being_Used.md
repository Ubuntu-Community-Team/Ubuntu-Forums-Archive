---
title: "Memory Upgrade- Memory Not Being Used?"
date: 2011-03-31
forum: Hardware
---

### Post by noleks on 2011-03-31
Hi:
I just upgraded my memory from 1GB to 4GB.  For some reason the system is only reporting 2.8GB total:

[FONT=Courier New]noleks-ub:~> free -m
             total       used       free     shared    buffers     cached
Mem:          2770       1321       1448          0        169        571
-/+ buffers/cache:        580       2190
Swap:         2557          0       2557[/FONT]

Has anyone else seen this?  I read something about reconfiguring the kernel to use more memory, but I'm not sure whether the Update Manager can adapt to the new physical memory available, or whether I need to tweak and rebuild the kernel myself?
If the latter is the case, I then would have a couple additional questions:
1) What is the working directory for a kernel build, for instance I don't know the difference here in /usr/src:[INDENT]drwxr-xr-x 24 root root 4096 2011-03-30 23:25 linux-headers-2.6.32-30
drwxr-xr-x  7 root root 4096 2011-03-30 23:26 linux-headers-2.6.32-30-generic

[/INDENT]2) If I run make menuconfig or whatever, will the settings used for the previous kernel build be maintained (ie I can tweak just what I need to tweak)?

Thanks!

---

### Post by Yellow Pasque on 2011-03-31
This is expected behavior for a 32-bit system (also looks like you have some memory going to onboard video). Install 64-bit distro or use PAE: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by noleks on 2011-03-31
Uh-oh...
Well it looked like everything was going swimmingly until I rebooted.  I installed pae headers and it looks like it rebuilt the kernel.  But now I get this:

Ubuntu 10.04.2 LTS noleks-ub tty1

noleks-ub login: [  24.540101 cx25840 2-0044: 0x0000 is not a valid video input!
[ 135.328566] cx25840 2-0044: 0x0000 is not a valid video input!


I can login so hopefully I can back out or repair what happened at the command line?

HELP!!

P.S. "free -m" now reports 3764MB total, so pretty sure pae IS working!

---

### Post by Yellow Pasque on 2011-03-31
It looks like your video tuner card is not liking the PAE kernel. Just boot into the old kernel.

---

### Post by noleks on 2011-03-31
Hi:
Looking at the undo procedure in the "Enabling PAE" howto I noticed I was missing one package:

linux-headers-generic-pae 2.6.32.30.36

This seems to have fixed things.

Thanks!!

---

