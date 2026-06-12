---
title: "Lost add/remove, synaptic, not in sudoers list HELP!!!"
date: 2008-07-27
forum: General Help
---

### Post by schreckles on 2008-07-27
Well, I just realized I'd lost add/remove from the applications menu...I thought no biggie...go to the menu list and fix it...wrong. It automatically unchecks itself every time. So I figured I'd delete and recreate it...except being the genius I am, I don't know what to put as the actual command. Same thing happened with the Sources List and Synaptic Package Manager under system->admin. Decided I would try to fix it by seeing if```
sudo apt-get upgrade
``` and ```
sudo apt-get update
``` would work at all to no avail. It comes back with "darrel is not in the sudoers file.  This incident will be reported."

Please somebody help me fix this!!!

---

### Post by iaculallad on 2008-07-27
For you not included in the sudoer file, Try to login using the recovery mode and input the command below:

```

sudo adduser darrel admin
sudo shutdown -r now

```

That will include you to the admin group.

---

### Post by schreckles on 2008-07-28
> **iaculallad said:**
> For you not included in the sudoer file, Try to login using the recovery mode and input the command below:

```

sudo adduser darrel admin
sudo shutdown -r now

```

That will include you to the admin group.

Thanks a lot...that did the trick...and right after that I decided I wanted to try out KDE4 finally anyway..LOL. So it was all moot...but at least I learned to solve another problem.

---

