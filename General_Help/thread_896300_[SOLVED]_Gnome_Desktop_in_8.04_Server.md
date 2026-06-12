---
title: "[SOLVED] Gnome Desktop in 8.04 Server?"
date: 2008-08-21
forum: General Help
---

### Post by william_hunter on 2008-08-21
I can't seem to enable the Gnome desktop in 8.04. I installed it, and configured it, but it won't start. Is there a walkthrough that I am somehow missing here?

---

### Post by Vivaldi Gloria on 2008-08-21
> **william_hunter said:**
> I can't seem to enable the Gnome desktop in 8.04. I installed it, and configured it, but it won't start. Is there a walkthrough that I am somehow missing here?

Server comes without any desktop environments. Is there a reason you didn't install the dsktop cd?

---

### Post by william_hunter on 2008-08-21
Because server comes with more of the packages I want pre-installed, like LAMP. I've done this before, and the reason for installing desktop is so a few remote users that are windows people  can feel comfortable working in the system.

---

### Post by Vivaldi Gloria on 2008-08-21
> **william_hunter said:**
> I can't seem to enable the Gnome desktop in 8.04. I installed it, and configured it, but it won't start. 

How did you install it?

To install use

```
sudo apt-get install ubuntu-desktop
```

---

### Post by william_hunter on 2008-08-21
Actually, as it turns out...I had used the correct command, but it didn't work right. I re-installed the OS and then everything went as it should have. 

Yes, I did use 'sudo apt-get install ubuntu-desktop'

---

### Post by Vivaldi Gloria on 2008-08-21
> **william_hunter said:**
> I re-installed the OS and then everything went as it should have. 

Glad to hear that. Please mark this thread as [SOLVED] using the thread tools.

---

