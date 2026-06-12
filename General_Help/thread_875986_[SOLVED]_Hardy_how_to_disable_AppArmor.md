---
title: "[SOLVED] Hardy: how to disable AppArmor????"
date: 2008-07-31
forum: General Help
---

### Post by johann_p on 2008-07-31
It seems that Hardy has silently introduced AppArmor and now I am unable to run mysql like I want anymore. The problem is that obviously AppArmor prevents mysql from using files that reside on a different disk.

However, because of size and backup considerations I need to have parts of mysql on various other disks!

I am desperately trying to re-create the installation I had running under Gutsy under a freshly installed Hardy and this is one of the major stumbling blocks!

I also read that there are problems with cups and AppArmor -- so instead of tinkering with it, can I just disable it entirely? I definitely dont need it, thank you very much.

---

### Post by FakeOutdoorsman on 2008-07-31
You can disable the AppArmor framework with (from [AppArmor: Ubuntu Community Documentation]("https://help.ubuntu.com/community/AppArmor")):
```
sudo /etc/init.d/apparmor kill
sudo update-rc.d -f apparmor remove
```
Haven't tried it myself.  Instead, I just purged all AppArmor packages.  Didn't have any problems, but I haven't been using mySQL.

---

### Post by johann_p on 2008-07-31
Thank you that did it.

---

### Post by martin_lindhe on 2009-10-07
I ended up here having the same trouble as the threadstarter (mysql db on non-default location).

I wanted to add that you can instead set mysql to complain mode in apparmor, which will allow but log instead of blocking (default).

  sudo aa-complain /usr/sbin/mysqld

This will result in a working mysql and apparmor.

---

### Post by chongman99 on 2010-03-12
Thanks for the sudo aa-complain suggestion.

How would I put this in my startup sequence so I don't have to type this each time? I've never messed with init.d before, but I think that's where I would go.

---

