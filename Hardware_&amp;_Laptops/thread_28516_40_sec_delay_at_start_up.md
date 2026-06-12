---
title: "40 sec delay at start up"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by cheniz on 2005-04-20
I have a really annoying problem. At system start up, after it says "Starting Ubuntu..." it just stops and waits for exactly 40 seconds doing nothing, then continues loading ubuntu.

this started happening today.
does this have anything to do with this bug?
[https://bugzilla.ubuntu.com/show_bug.cgi?id=6879](https://bugzilla.ubuntu.com/show_bug.cgi?id=6879)

if yes, is there any patch to resolve this?
i also dont see icons of my mounted fat32 and ntfs partitions on desktop. and in computer, the names of the partitions are like "17GB media", not the names of the folders where they are mounted.
i guess this is the reason: [https://bugzilla.ubuntu.com/show_bug.cgi?id=7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641)

so what should i do to fix these two problems? the second one is not that important but the 40 seconds waiting at the boot up is a real problem. 

i'm using a toshiba satellite 2410-404 laptop, have dual boot with win xp.
thanks for helping.

---

### Post by accuser on 2005-04-20
During the message you are seeing and the next, the kernel is booting. In days gone by, you would have seen all the kernel messages as devices initialised. You can see these messages by typing the following at the console:
```
$ dmesg | less
```
You can also dump these messages to a text file in your home directory to post back here for more help:
```
$ dmesg > ~/dmesg.txt
```

---

