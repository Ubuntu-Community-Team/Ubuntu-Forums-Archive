---
title: "A problem with file system."
date: 2013-07-09
forum: Hardware
---

### Post by lampadron on 2013-07-09
Hi everyone a few day ago I have checked the propriety of some files on my Pc and i find out that the total size of files are smaller than space occupied on my hard disk. When I tried to check my hard disk with disk utility it said that "file system is not clean" :(. 
Somebody could explain what i have to do to fix this problem :confused:?

Thank for your future replies :P!

---

### Post by Bashing-om on 2013-07-09
lampadron; Hi !

A quick simpler "attempt" to fix the file system:
terminal codes:
```

sudo touch /forcefsck 
sudo shutdown -r now

```to force a file system check at next reboot.
Else, will use a direct application of fsck to effect the repair.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by lampadron on 2013-07-10
Hi and thanks for your reply:P . It looks like the problem is gone, I mean now the file system is clean, but "total size of file" value and "size on disk" value of all files are still different. The last one is always bigger then the first one, and it also unreal. I mean it shows me that I have 8 TB occupied on my 1 TB hard drive :confused:. 
Can you explain why "size on disk" value stand for? I thought it stand for the real size of file stored on my hard drive, but in that case it should be more similar to the "total size of file" value.


P.S. 
I'm using lubuntu and I find "size on disk" value in window of propriety.

---

### Post by Bashing-om on 2013-07-10
lampadron;

Good the system is good.
As to the disparity in reported file sizes // can not come close to that one !

However, for  CLI tools to look at files' sizes see this thread:
[thread]12723222[/thread] 

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by lampadron on 2013-07-12
Thanks :)

---

