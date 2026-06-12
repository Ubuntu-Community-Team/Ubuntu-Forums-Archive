---
title: "[SOLVED] How do I tell if LTS?"
date: 2008-08-04
forum: General Help
---

### Post by 3rods on 2008-08-04
How can I tell if I'm running the LTS version of ubuntu? 

When I do uname -a it gives me a rather vague:
```
2.6.24-19-generic #1 SMP Wed Jun 18 14:40:41 UTC i686 GNU/Linux
```

---

### Post by kostkon on 2008-08-04
> **3rods said:**
> How can I tell if I'm running the LTS version of ubuntu? 

When I do uname -a it gives me a rather vague:
```
2.6.24-19-generic #1 SMP Wed Jun 18 14:40:41 UTC i686 GNU/Linux
```
Yes, from your kernel version I can see that you use 8.04. But to check it yourself, you can go to *System -> Administration -> System Monitor* and look in the first tab, or open a terminal and give
```
lsb_release -a
```

---

### Post by pdwerryhouse on 2008-08-04
Look at /etc/issue instead:

```
cat /etc/issue
```

LTS versions are 6.06 and 8.04.

---

### Post by 3rods on 2008-08-04
> **pdwerryhouse said:**
> Look at /etc/issue instead:

```
cat /etc/issue
```

LTS versions are 6.06 and 8.04.

Oh. So 8.04.1 isn't LTS only 8.04?

---

### Post by kostkon on 2008-08-04
> **3rods said:**
> Oh. So 8.04.1 isn't LTS only 8.04?
It is.

---

### Post by 3rods on 2008-08-04
Thank you. That must have sounded thick-headed. I didn't know how the versions worked.

This made it very clear for anyone else who doesn't know:
[http://blog.canonical.com/?p=15]("http://blog.canonical.com/?p=15")

---

### Post by pi.boy.travis on 2008-08-04
8.04.1 is an updated ISO, so new installs don't need to install so many updates.

---

### Post by cariboo on 2008-08-04
THe 8.04 LTS release was quite buggy at release time. the point release was to clear up a lot of the bugs.

Jim

---

