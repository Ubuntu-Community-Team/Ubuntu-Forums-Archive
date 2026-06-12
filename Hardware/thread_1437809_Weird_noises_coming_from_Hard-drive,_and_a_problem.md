---
title: "Weird noises coming from Hard-drive, and a problem."
date: 2010-03-24
forum: Hardware
---

### Post by Pranka on 2010-03-24
First off, I only encounter this problem in Ubuntu. I had installed Arch, and everything worked like a miracle.
(Not going to explain why I switched back to Ubuntu)
After logging in, and the desktop loads, I start hearing weird noises from my hard-drive every few minutes. When the noise is constant, that's when my second problem appears.
The second problem is, /home switches from rw (read-write) to ro (read-only), and I can't save any of my files on it. Needless to mention, this only happens to my on Ubuntu.
Few specifications of my laptop:
 - HP Pavilion Entertainment PC
 - Ubuntu 9.10
Fstab:
```

# /home was on /dev/sda7 during installation
UUID=bdac632d-2267-478b-8755-bfbdb8b4f904 /home           ext4    defaults        0       2

```

The only thing I can do to make it stop (for a short while only), is by rebooting into Ubuntu. If anyone knows a solution to it, please do share, for I am running out of options.
I can't simply restart every few minutes, and I have lots to do.

---

### Post by ajgreeny on 2010-03-24
What, if anything, does palimpsest say about the drive?  Go to System ->Administration ->Disk Utility, and you can run a disk check.

---

### Post by n0dix on 2010-03-24
Weird thing. Do you get any message from S.M.A.R.T.? S.M.A.R.T. is a program that alerts you when your hard drive have a critical problem. This message usually appear in console. This programs run automatically, you don't have to run it.

---

### Post by khemcloud on 2010-03-24
Hard rive noise is not good. Often means pending disk failure. Advise you backup any data files.

---

