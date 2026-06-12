---
title: "Help! Serial port promblems"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by Toshick on 2007-11-09
I've tried to search in this forums and Net something like this, but i didn't find any solution for this problem. 
There was a similar thread, but it was at another (i think now right) thread of this forum:
[http://ubuntuforums.org/showthread.php?t=504492&highlight=serial+port&page=2](http://ubuntuforums.org/showthread.php?t=504492&highlight=serial+port&page=2)

I have problem on Gutsy x64. My serial port works into one way - i can send commands to modem, and my modem do, what i want, but i dont see responds from modem. I have the same trouble as people few posts up:

#ls -l /dev/ttyS*
crw------- 1 root root 4, 64 2007-11-09 02:05 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2007-11-07 21:12 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2007-11-07 21:12 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2007-11-07 21:12 /dev/ttyS3

#cu -l ttyS0 -s 19200
cu: open (/dev/ttyS0): Permission denied
cu: ttyS0: Line in use

I've tried to find solution about one week, tried different way:
removing blrtty, add getty to inittab (init.d) end etc.
Please, people who find solution, can you share with it?
Maybe in this thread somebody know what to do.

Thank you in advance...

---

### Post by Toshick on 2007-11-13
Help!

---

