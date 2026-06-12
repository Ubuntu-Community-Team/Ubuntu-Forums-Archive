---
title: "Formated WD external hd, can't put anything on it."
date: 2009-08-07
forum: Hardware
---

### Post by RPG Master on 2009-08-07
So I just bought a Western Digital 640gig My Book. I knew the first thing I wanted to do is format to ext3, so I did... After it was done I went to put a file on it, but then I got an error saying that I didn't have permission :(

What's wrong?

---

### Post by Bucky Ball on 2009-08-07
```
sudo chmod -R +w /media/usbdrive

```Where USBdrive is the mount point name. Many suggestions here:

[http://ubuntuforums.org/showthread.php?t=88531&page=2](http://ubuntuforums.org/showthread.php?t=88531&page=2)

Wouldn't know the definitive. Someone might like to help us out on that. :)

---

### Post by RPG Master on 2009-08-08
Very sorry but I got my solution from #ubuntu :)

---

### Post by amac777 on 2009-08-08
Just curious, what was the solution?

---

### Post by RPG Master on 2009-08-09
> **amac777 said:**
> Just curious, what was the solution?

Something very similar to Bucky Ball's post... I can't really remember :P

---

