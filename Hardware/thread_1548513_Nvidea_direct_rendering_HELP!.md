---
title: "Nvidea direct rendering HELP!"
date: 2010-08-08
forum: Hardware
---

### Post by ryanman on 2010-08-08
hello all! I am trying to get direct rendering to work on my laptop.  I am using ubuntu 10.4 and have a nvidea geforce 9600m gt.  Can anyone help me out?

---

### Post by bprins on 2010-08-08
it might help to tell at least what goes wrong :)

what does 
```

glxinfo | grep rendering

```
give for output?

---

### Post by ryanman on 2010-08-08
:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

### Post by Fafler on 2010-08-08
Go to System -> Adminstration -> Hardware drivers and install the binary nvidia driver.

---

### Post by ryanman on 2010-08-08
> **Fafler said:**
> Go to System -> Adminstration -> Hardware drivers and install the binary nvidia driver.


laptop:~$ glxinfo | grep rendering
direct rendering: Yes

thank you very much worked like a charm i had installed the wrong driver doh!

---

