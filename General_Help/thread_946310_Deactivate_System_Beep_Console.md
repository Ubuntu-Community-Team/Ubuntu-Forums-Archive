---
title: "Deactivate System Beep Console"
date: 2008-10-13
forum: General Help
---

### Post by Sanix on 2008-10-13
How can I disable the system beeps in all consoles?

---

### Post by homemadejam on 2008-10-13
> **Sanix said:**
> How can I disable the system beeps in all consoles?

System -> Preferences -> Sound -> System Beep Tab
And you should be able to enable / disable it from there.

Jam

---

### Post by Sanix on 2008-10-13
Thanks, but this doesn't work, if I open the console with ctrl + alt + f1

---

### Post by paris_alex on 2008-10-13
checkout this post for the solution...

[http://ubuntuforums.org/showthread.php?t=531781](http://ubuntuforums.org/showthread.php?t=531781)

Cheers!

---

### Post by Sam on 2008-10-13
Add at the end of the ~/.bashrc file:
```
# Disable beeps
setterm -blength 0
```

---

### Post by kpkeerthi on 2008-10-13
Add **pcspkr** to /etc/modprobe.d/blacklist

---

