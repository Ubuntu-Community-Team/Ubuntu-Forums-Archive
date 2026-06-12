---
title: "What is uuid?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by camper365 on 2009-05-07
I have noticed that on my GRUB menu.lst, instead of a 
```
root (hd0,4)
```
there is a 
```
uuid            58f83c3c-6456-4d33-b2c6-2cdb9625521d
```
Why is that, what is uuid? I have noticed that if I use the command-line to boot grub, and I use root (hd0,4) it doesn't start usplash and it looks like the recovery mode.

---

### Post by Mze on 2009-05-07
Read up on it [here]("http://en.wikipedia.org/wiki/Uuid")

---

### Post by sisco311 on 2009-05-07
> **camper365 said:**
> I have noticed that on my GRUB menu.lst, instead of a 
```
root (hd0,4)
```
there is a 
```
uuid            58f83c3c-6456-4d33-b2c6-2cdb9625521d
```
Why is that, what is uuid?


[uhelp]community/UsingUUID[/uhelp]
[http://www.linux.com/feature/146951]("http://www.linux.com/feature/146951")

> 
I have noticed that if I use the command-line to boot grub, and I use root (hd0,4) it doesn't start usplash and it looks like the recovery mode.

you have to add "ro quiet splash" to the kernel line. ;)

i.e.
```
root (hd0,0)
kernel /boot/vmlinuz-blabla root=/dev/sda1 ro quiet splash
initrd /boot/initrd.gz
boot

```

---

### Post by camper365 on 2009-05-07
thx

---

