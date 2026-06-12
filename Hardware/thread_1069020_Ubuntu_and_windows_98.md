---
title: "Ubuntu and windows 98"
date: 2009-02-13
forum: Hardware
---

### Post by glooorfindel on 2009-02-13
I was wondering how i would boot each one without opening the case and changing the cable from each hardrive and putting it on the one i want to boot

---

### Post by cariboo on 2009-02-13
Use grub, it is usually installed by default. Make sure both drives are connected, then boot from your LiveCD, once at the desktop, open an Applications-->Accessories-->Terminal and type:

```
sudo grub
```

This will get you to the grub prompt, next at the prompt type:

```
find /boot/grub/stage1
```

This will find what drive and partition grub is installed on. The next step type;

```
root (hd0,0)
```

replace (hd0,0) with the result you got from the find command, now setup the mbr, type:

```
setup (hd0)
```

where (hd0) is the result of the find command with out the partition number (second number). Finally type:

> quit

and reboot.

Jim

---

