---
title: "[SOLVED] How to display system information?"
date: 2008-08-14
forum: General Help
---

### Post by Killer Cop on 2008-08-14
I'm trying to figure out if my Ubuntu 8.04 is 32-bit or 64-bit.

But there is NOTHING on this matter, I can't find ANYTHING about it either here on these forums, Google, NOTHING. Can't see anything in system monitor. How the **** do I display that system information?!!! :confused:

---

### Post by cdtech on 2008-08-14
Just type "uname -a" you should see:
```
Linux laptop 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_**64** GNU/Linux
```
(the bold shows what your looking for)

---

### Post by Killer Cop on 2008-08-14
Thanks for the quick reply.

But it won't work!!! It displays this:

```
Linux FIRESTORM 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

---

### Post by cdtech on 2008-08-14
Your not running "64" your running "32".
(**i686**)

---

### Post by cpetercarter on 2008-08-14
There is a rather nice utility called hardinfo which will tell you everything about the hardware on your system and then some, and allow you to generate and print out reports..
```
sudo apt-get install hardinfo
```
To run, just type in a terminal
```
hardinfo
```

---

### Post by Killer Cop on 2008-08-14
Oh. Well, thanks for the help. A thanks flying your way.

---

### Post by lukjad on 2008-08-14
```
Linux FIRESTORM 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 **i686** GNU/Linux
```

You have an i686 architecture.

[http://en.wikipedia.org/wiki/Intel_P6](http://en.wikipedia.org/wiki/Intel_P6)

EDIT: Beaten again.

---

### Post by sayakb on 2008-08-14
Please mark the thread as solved (Thread tools->Mark thread as solved)

---

