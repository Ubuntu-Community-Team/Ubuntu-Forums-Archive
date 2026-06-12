---
title: "[SOLVED] VNC and SSH delay on connect"
date: 2008-10-10
forum: General Help
---

### Post by tmcmulli on 2008-10-10
I have one 7.10 desktop that shows a 10s delay when I connect via VNC or SSH.  None of my other machines (or any VMs I install) show this same behavior.  I use Fail2Ban and hosts.deny, but again, I use those on all my machines... just looking for where I should look to find out what's different about this system...

Thanks!

---

### Post by Sam on 2008-10-10
Hum maybe it's because of IPv6...

Try [this](http://ubuntuforums.org/showthread.php?t=87798)

or try to run SSH with the "-4" switch to force IPv4:
```
ssh -4 user@host
```

---

### Post by tmcmulli on 2008-10-10
That did it!  I had to actually disable in /etc/modprobe.d, just the simple -4 didn't work... but all is perfect now...

Thanks!

---

### Post by Sam on 2008-10-10
You're welcome! ;)

---

