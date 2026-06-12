---
title: "kernel panic question"
date: 2008-10-10
forum: Hardware
---

### Post by zero7404 on 2008-10-10
does ubuntu create log files or dump info when a kernel panic happens ?

is a kernel panic the equivalent of a windows freeze ? when i get a kernel panic i shut down the machine and restart...not sure if there's a certain keystroke or period of time to wait before things go back to normal ?

i'll do a memtest and see if there's any issues there...

---

### Post by sokopok on 2008-10-10
A kernel panick is like a Windows blue screen.
You can check the logs in /var/log (especially messages, dmesg, syslog)

---

### Post by zero7404 on 2008-10-10
> **sokopok said:**
> A kernel panick is like a Windows blue screen.
You can check the logs in /var/log (especially messages, dmesg, syslog)

thanks

i'm assuming some hardware on my machine is causing this issue. i did a memtest and the memory is fine, so it must be something else....

---

