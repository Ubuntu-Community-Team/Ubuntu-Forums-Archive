---
title: "Floppy drive writing issues"
date: 2019-11-09
forum: Hardware
---

### Post by mariofanboy-21 on 2019-11-09
Hello everyone, since a floppy drive was installed on a Dell Inspiron 540, I have been using it to read old floppy drives I have lying about. However in regards to being able to successfully write to the disk, I keep getting into the issue that  the entire drive  is owned by root, making it impossible to  successfully write to it without invoking  root access. How can I get my floppy drive to be used by  normal users.

[https://i.imgur.com/Lu5QnmE.png](https://i.imgur.com/Lu5QnmE.png)

---

### Post by uRock on 2019-11-09
Have you tried chowning it? [https://www.howtoforge.com/linux-chown-command/](https://www.howtoforge.com/linux-chown-command/)

---

### Post by mariofanboy-21 on 2019-11-09
> **uRock said:**
> Have you tried chowning it? [https://www.howtoforge.com/linux-chown-command/](https://www.howtoforge.com/linux-chown-command/)

No, I haven't

---

### Post by Holger_Gehrke on 2019-11-09
Unless something changed since 14.04 - which I've still got on an old P4 Laptop that I only use when I need a floppy, a serial port or a parallel port - there should be a line in /etc/fstab like this:
```
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```
Since I don't remember putting that in myself it was probably put there during installation. This means that the drive can be mounted by a normal user without sudo. If I mount a floppy from the file manager, it ends up being owned by root, but if I mount it from the command line with a simple 'mount /dev/fd0' (**no** sudo), it's owned by my account.

Holger

---

### Post by TheFu on 2019-11-09
Beware:  [https://www.theregister.co.uk/2019/07/30/torvalds_floppy/](https://www.theregister.co.uk/2019/07/30/torvalds_floppy/)
> Linus Torvalds has articulated what much of the world has known for some time, with a merge marking the Linux floppy driver as "orphaned".
If you have any programs or data still on floppy disks, best to move that onto newer media soonish.

---

