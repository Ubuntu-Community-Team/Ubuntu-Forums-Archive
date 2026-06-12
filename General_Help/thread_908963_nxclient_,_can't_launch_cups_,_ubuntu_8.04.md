---
title: "nxclient , can't launch cups , ubuntu 8.04"
date: 2008-09-03
forum: General Help
---

### Post by sles on 2008-09-03
Hello!

I want to get cups printing with nxclient  3.2.0-13.
But I get Can't launch cups server 
on client side.

Looks like it tries to start
cupsd -c /home/dm/.nx/cups/cupsd.conf
cupsd: Child exited with status 1!


How can I solve this problem?

btw, my colleague have the same problem with Ubuntu 7.10..

---

### Post by cariboo on 2008-09-03
Have you tried in a terminal:

```
sudo /etc/init.d/cupsys start
```

on the client?

You could also log in using ssh and use the same command.

Jim

---

### Post by sles on 2008-09-03
> **cariboo907 said:**
> Have you tried in a terminal:

```
sudo /etc/init.d/cupsys start
```

on the client?



As I understand this will start system wide cups, not cups from user, as nxclient does.

> 

You could also log in using ssh and use the same command.



On server? Why? nxclient  can't start cups for me at client side...

---

### Post by sles on 2008-09-05
Excuse me, nobody uses nxclinet on ubuntu?

---

### Post by geofftech on 2009-07-26
I have 9.4 and cupsys is called cups

try running

```
sudo ln -s cups cupsys
```

as a dirty fix

---

