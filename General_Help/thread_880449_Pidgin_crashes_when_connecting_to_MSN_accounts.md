---
title: "Pidgin crashes when connecting to MSN accounts"
date: 2008-08-05
forum: General Help
---

### Post by jerome1232 on 2008-08-05
I've just recently started having pidgin segfault when I first start it up.

First thing I tried was to start with fresh config files
```
mv .purple .purple-bck
```

This got me up and running, and all works great until I try to add an MSN account, soon as I finish the account and hit add; instant crash. I also tried removing/reinstalling pidgin with the --purge option.

It seems to be happening to a few other people. [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/202796](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/202796)

For what it is worth, it doesn't crash while running it this way:
```
G_SLICE=always-malloc G_DEBUG=gc-friendly valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log.pidgin pidgin
```

Pidgin works fine on other user accounts. Does anyone have an idea of what in my profile could cause this behavior? 

If I don't get this figured out I guess I will be backing up my /home and recreating my user in a few days as I use pidgin with MSN accounts alot. I would like to figure out exactly what is causing this though.

---

### Post by prshah on 2008-08-05
> **jerome1232 said:**
> 
Pidgin works fine on other user accounts. Does anyone have an idea of what in my profile could cause this behavior? 


I'd suggest looking through your plugins, especially the AWN plugin if you have it installed and are using it.

---

### Post by bismark on 2008-08-27
> **jerome1232 said:**
> I've just recently started having pidgin segfault when I first start it up.

First thing I tried was to start with fresh config files
```
mv .purple .purple-bck
```

This got me up and running, and all works great until I try to add an MSN account, soon as I finish the account and hit add; instant crash. I also tried removing/reinstalling pidgin with the --purge option.

It seems to be happening to a few other people. [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/202796](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/202796)

For what it is worth, it doesn't crash while running it this way:
```
G_SLICE=always-malloc G_DEBUG=gc-friendly valgrind -v --tool=memcheck --leak-check=full --num-callers=40 --log-file=valgrind.log.pidgin pidgin
```

Pidgin works fine on other user accounts. Does anyone have an idea of what in my profile could cause this behavior? 

If I don't get this figured out I guess I will be backing up my /home and recreating my user in a few days as I use pidgin with MSN accounts alot. I would like to figure out exactly what is causing this though.


I'm was having the same issue, use to work, now it doesn't.  I removed everything and tried to reconfigure but the instant I add an MSN account it segfaults.

I ended up fixed it by enabled the hardy backports repository in /etc/apt/sources.list and updating pidgin, pidgin-data, and libpurple0 and then commenting out backports again.

So far..... no problems.

---

### Post by jerome1232 on 2008-08-27
I'll remember that, if it ever happens to me again, I ended up reinstalling over it. I'm pretty sure it was something I changed somewhere, just no way to trace my steps back.

---

### Post by gardara on 2008-08-27
Do you have the facebook-chat plugin installed? It's known to cause crashes....

---

### Post by jerome1232 on 2008-08-27
Oh I never did answer about plugins I didn't have any plugins enable that aren't turned on by default (if any are turned on by default)

---

### Post by gardara on 2008-08-27
You can check the #pidgin channel at FreeNode... They are quite useful and give fast support :)

---

