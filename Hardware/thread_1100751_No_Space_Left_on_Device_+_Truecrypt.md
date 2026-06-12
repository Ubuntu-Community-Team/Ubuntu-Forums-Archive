---
title: "No Space Left on Device + Truecrypt"
date: 2009-03-19
forum: Hardware
---

### Post by BrandonBan6 on 2009-03-19
Man oh man...

So here is my df output:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             92196516  91631136         0 100% /
tmpfs                  1011612         0   1011612   0% /lib/init/rw
varrun                 1011612       340   1011272   1% /var/run
varlock                1011612         0   1011612   0% /var/lock
udev                   1011612      2908   1008704   1% /dev
tmpfs                  1011612       104   1011508   1% /dev/shm
lrm                    1011612      2384   1009228   1% /lib/modules/2.6.27-11-generic/volatile
overflow                  1024        32       992   4% /tmp


```

I'm getting a "No Space left on Device error" here and there. THe only thing I can think of is, I installed Truecrypt this morning, I just installed i didn't encrypt anything yet. Not sure where to go from here :(.

---

### Post by BrandonBan6 on 2009-03-19
Perhaps a I jumped the gun...

I went in and cleaned up some files......and everything is back to normal. The entire drive didn't seem to be in use, but whatever, chalk this one up as solved.

---

