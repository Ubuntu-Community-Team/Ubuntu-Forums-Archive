---
title: "Is it possible DVD writer shutting down PC?"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by bengrech on 2008-01-14
Dear All,

Wanted to ask a question regarding an Ubuntu box running 2.6.15-26-amd64-generic.  This box is configured as a server and runs a weekly backup onto a DVD.  For about 4~5 weeks works fine but then after a failed burn, next morning I find this box shutdown!?

Is there any way a failed burn or a failing drive could be shutting it down.  What could I do to trace what is the problem?

Anyone's help would be greatly appreciated for this glitch I have been living with recurringly.

---

### Post by jackflap on 2008-01-14
To be honest, anything's possible, especially when the hardware drivers are located inside the kernel (as they are in Linux).

Have you reproduced this? Is it consistent that whenever the burn fails, the computer shuts down? Could the computer be shutting down, and in turn destroying the burn? Does it shutdown sometimes without actually managing to burn anything?

Alex

---

### Post by kostkon on 2008-01-14
You could check your system logs that you can find at
```
/var/log
```

---

