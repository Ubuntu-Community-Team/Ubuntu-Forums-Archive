---
title: "[SOLVED] ipod help"
date: 2008-10-16
forum: General Help
---

### Post by rick08 on 2008-10-16
I am trying to install the rockbox bootloader on my ipod.  I have followed all the installation steps in the manual, but ipod patcher doesn't find my ipod. This is what the terminal spit out.
```
ricky@ricky-laptop:~$ cd $HOME
ricky@ricky-laptop:~$   chmod +x ipodpatcher
ricky@ricky-laptop:~$   ./ipodpatcher
ipodpatcher v3.0 with v3.0 bootloaders - (C) Dave Chapman 2006-2007
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] Scanning disk devices...
[ERR]  FATAL: Permission denied on 2 device(s) and no ipod detected.
[ERR]  You need permissions for raw disc access for this program to work!

Press ENTER to exit ipodpatcher :

```
I would appreciate any help.

---

### Post by chazn85 on 2008-10-16
Could be stating the obvious here but have you tried to run as root?

---

### Post by rick08 on 2008-10-16
Wow.  That is a total noob mistake.  I'll check to see if running as root changes anything.

---

### Post by chazn85 on 2008-10-16
could be you get a different error or your user just isnt permissioned properly for the device

---

### Post by rick08 on 2008-10-16
Thanks for the help.  Seems that I wasn't root.

---

