---
title: "irda not working"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by [h2o] on 2006-08-20
I was going to sync evolution with my phone, so I installed irda-utils and multisync.
Unfortunately, it seems like an old bug I filed during the Dapper Beta is still there: Loading irda-utils (sudo /etc/init.d/irda-utils start) starts the kIrDad process which uses 80-100% CPU and hangs the computer after a while.
Any ideas about what to do?
The computer is an Asus A6k.

---

### Post by JuanFerS on 2006-08-31
I had to compile irda-utils from source and start it whenever I want to sync my palm.  I don't know why this happens... but it's a way to get around this problem.

---

### Post by [h2o] on 2006-09-01
Did you have the same issues as I had (with kIrDad eating CPU) or was it just not working?
I might try compiling it from source though, thanks for the tip :)

---

### Post by JuanFerS on 2006-09-02
kIrDad was using around 90% of the processor (P4 3.2 HT) using SMP kernel.
The problem is not kIrDad... it's in the way irda-utils runs or initializes, when I compile irda-utils from source and simple type in the "irattach" command everything works OK. when i use the startup script supplied by the .deb file kIrDad eats the CPU.
I had to make a simple script to load irattach at startup.
My computer is an Asus A4L so I guess it might work on yours too.

---

### Post by [h2o] on 2006-09-02
I guess I'll just have to try that right away :)

---

