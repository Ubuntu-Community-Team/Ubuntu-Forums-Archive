---
title: "Wubi partial install problem"
date: 2008-10-19
forum: General Help
---

### Post by tim.a on 2008-10-19
Hello everyone!

Just tried to install Wubi for the first time.  initial install and restart worked fine.  I got to the Heron background, where the one load box is visible and thats it.  System install went quick, second load also, then it went to 'formating space in partition for disks/ubuntu.... and it never starts.  Its stuck stays at 0% (i left it for about 15 minutes)  any ideas?

---

### Post by ago on 2008-10-20
> **tim.a said:**
> Hello everyone!

Just tried to install Wubi for the first time.  initial install and restart worked fine.  I got to the Heron background, where the one load box is visible and thats it.  System install went quick, second load also, then it went to 'formating space in partition for disks/ubuntu.... and it never starts.  Its stuck stays at 0% (i left it for about 15 minutes)  any ideas?

What version of wubi is this? You can press ctrl+alt+f4 to get a terminal and have a look at the log for more info

less /var/log/syslog

(go to the bottom)

---

