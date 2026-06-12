---
title: "grub file"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by overclock17 on 2009-02-02
i had just formated my laptop and made 3 5ogb partions on one i installed xp and it worked fine on the other i installed ubuntu 8.10 and it worked great then now i decided to install windows 7 on the third one so i went on reformated and installed it
now when i turn on the laptop i cant go into ubuntu anymore i see both windows but no ubuntu 
i asked my friend about it and he said i need to get into grub file somehow and put a code in there
can any one help me with that please?
and if this is not the problem then what is the problem?
thanks

---

### Post by Stolea on 2009-02-02
When You boot, do you get the the grub choice of operating systems, i.e Ubuntu, WinXp and Vista?

---

### Post by cariboo on 2009-02-02
You overwrote the mbr when you installed Windows 7. To restore grub, get out your LiveCD and boot from it. Once at the desktop open an Applications-->Accessories-->Terminal and type:

```
sudo grub
```

Once at the grub prompt type:

```
find /boot/grub/stage1
```

This should result in something like this:

```
(hd0,1)
```

For the next step type:

```
root (hd0,1)
```

substitute the result of the find command for (hd0.1). Next type:

```
setup (hd0)
```

Use the result of the find command without the partition number. Once the command has run type:

```
quit
```

Reboot and you should have your grub menu back.

Jim

---

### Post by overclock17 on 2009-02-02
thank you jim 
gone to try it

---

