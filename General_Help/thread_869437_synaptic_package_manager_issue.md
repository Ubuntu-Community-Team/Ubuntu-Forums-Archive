---
title: "synaptic package manager issue"
date: 2008-07-24
forum: General Help
---

### Post by prometheus3 on 2008-07-24
Hello Forum,

X-Windblows user and a very happy long overdue Linux user! I can't believe I never took the plunge until now!

I'm having a few issues I hope someone can help me with??? I can no longer open or run synaptic package manager without encountering this message error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried running  "Sudo apt-get clean all" with no luck! I'm such a big newb! Please somebody help!!!

thanks,
-mike.

---

### Post by scragar on 2008-07-24
```
sudo dpkg --configure -a
```

---

### Post by prometheus3 on 2008-07-24
Thank you very much for the help, problem solved!!! I was typing that same command in the terminal, just a little different!!

---

