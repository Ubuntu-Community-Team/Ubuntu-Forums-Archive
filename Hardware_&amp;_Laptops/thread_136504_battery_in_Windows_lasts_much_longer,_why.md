---
title: "battery in Windows lasts much longer, why?"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by zasf on 2006-02-26
hi all,

I've been using Ubuntu for a while and I really enjoy it. The only issue I still have is battery life, in Windows can live almost exacly double time then ubuntu.

[IMG]http://www.webalice.it/mzandi/batteria.bmp[/IMG] [IMG]http://www.webalice.it/mzandi/batteriaUbuntu.png[/IMG]

My laptop is a brand new Toshiba Satellite M40-281, battery in win lasts in 2h:30m while in ubuntu lasts in 1h:30m

How can I investigate this and find a solution?
Do you have any ideas?

Thank you.

---

### Post by Denta on 2006-02-26
Are you using the right kernel for your machine?

Have you tried enabling laptop-mode? It saves your battery slightly by having a buffer in ram before writing to the disk.

**sudo laptop-mode start**

---

### Post by zasf on 2006-02-26
[QUOTE=Denta]Are you using the right kernel for your machine?

Have you tried enabling laptop-mode? It saves your battery slightly by having a buffer in ram before writing to the disk.

**sudo laptop-mode start**[/QUOTE]

I didn't know that command but it seems to be already active

```
matteo@uguzzoni:~$ sudo laptop_mode start
enabled, active [unchanged].
```

---

### Post by chopsbuntu on 2006-02-26
[QUOTE=Denta]Are you using the right kernel for your machine?

Have you tried enabling laptop-mode? It saves your battery slightly by having a buffer in ram before writing to the disk.

**sudo laptop-mode start**[/QUOTE]

Funny, when I do that on my laptop, it just says "Starting laptop-mode" and that's it. :-k

---

### Post by Vorian on 2006-02-26
try this in your terminal

```
fortune
```




now that the fun is over, you may have to configure your acpi.

---

