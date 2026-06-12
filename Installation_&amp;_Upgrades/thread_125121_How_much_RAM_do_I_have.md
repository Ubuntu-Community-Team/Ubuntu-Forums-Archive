---
title: "How much RAM do I have?"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by ollijav on 2006-02-03
I know I have 64 Mb RAM in my machine. I am going to put some more in, but how do I know whether it is working? Where to look in Gnome? Or is there a command I can type in the console, telling the amount of RAM in the machine?

---

### Post by barbarossa on 2006-02-03
```
free
```

---

### Post by kaamos on 2006-02-03
or better yet
```
free -m
```

---

### Post by az on 2006-02-03
You can also check in your bios, just as you boot.  You usually can display your system information (CPU, RAM, etc...)


You can also use the grub menu option for memtest86.  It is installed on your system.  Just hit escape to reveal the grub menu if it is not already revealed and select memtest.  I always let it run for an hour or more when I add memory to a box.

---

### Post by Eazy© on 2006-02-03
eazy@linux:~$ free -m
                  total       used       free     shared    buffers     cached
Mem:           1012        535        476            0          69         293
-/+ buffers/cache:        172        839
Swap:          1027           0       1027
------------------------------------------------------------------

Does this mean that I have 476 Mb or 839 Mb free for other programs?

Never really understod how much ram I have free. I run a systemstat thing with SuperKaramba that says I have 476 Mb free

Sorry for stealing the thread with a stupid question :P

---

