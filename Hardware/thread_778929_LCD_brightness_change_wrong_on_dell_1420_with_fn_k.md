---
title: "LCD brightness change wrong on dell 1420 with fn key"
date: 2008-05-02
forum: Hardware
---

### Post by insulae on 2008-05-02
Hi, i have a problem, when i press fn+down on my dell 1420 with Hardy the bright is going down from 100% to 30% approximately with only one press.
I want press fn+down or fn+up and change only a 10% of bright, where i can change this?

My friend have a dell 1520 with Kubuntu and he have the same problem.

Grettings
insulae

---

### Post by insulae on 2008-05-02
ok searching in the web i found in launchpad this solution:

```
edit /etc/modprobe.d/blacklist
```

and add the next line:

```

blacklist video

```

reboot and try fn+down fn+up work perfectly :D :D :D

---

