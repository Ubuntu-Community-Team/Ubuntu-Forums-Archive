---
title: "Songbird on Sabayon"
date: 2007-02-17
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2007-02-17
does anybody have it working? if so please post a HowTo.

---

### Post by mips on 2007-02-18
[http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer)

You might have seen that though.

---

### Post by RAV TUX on 2007-02-18
> **mips said:**
> [http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer](http://publicsvn.songbirdnest.com/trac/wiki/SettingUpGStreamer)

You might have seen that though.tried your link and got this message:


> Oops...

Trac detected an internal error:

malformed database schema - unable to open a temporary database file for storing temporary tables

Traceback (most recent call last):
  File "/usr/share/trac/cgi-bin/trac.cgi", line 20, in ?
    cgi_frontend.run()
  File "/usr/lib/python2.3/site-packages/trac/web/cgi_frontend.py", line 123, in run
    env = get_environment(req, os.environ, threaded=False)
  File "/usr/lib/python2.3/site-packages/trac/web/main.py", line 335, in get_environment
    return _open_environment(env_path, threaded)
  File "/usr/lib/python2.3/site-packages/trac/web/main.py", line 44, in _open_environment
    return open_environment(env_path)
  File "/usr/lib/python2.3/site-packages/trac/env.py", line 375, in open_environment
    if env.needs_upgrade():
  File "/usr/lib/python2.3/site-packages/trac/env.py", line 279, in needs_upgrade
    db = self.get_db_cnx()
  File "/usr/lib/python2.3/site-packages/trac/env.py", line 137, in get_db_cnx
    return self.__cnx_pool.get_cnx()
  File "/usr/lib/python2.3/site-packages/trac/db.py", line 157, in get_cnx
    cnx = self._cnx_class(**self._args)
  File "/usr/lib/python2.3/site-packages/trac/db.py", line 283, in __init__
    cnx = sqlite.connect(path, timeout=timeout)
  File "/usr/lib/python2.3/site-packages/sqlite/__init__.py", line 61, in connect
    return Connection(*args, **kwargs)
  File "/usr/lib/python2.3/site-packages/sqlite/main.py", line 445, in __init__
    self.db = _sqlite.connect(database, mode)DatabaseError: malformed database schema - unable to open a temporary database file for storing temporary tables

---

### Post by RAV TUX on 2007-02-21
More Songbird on Sabayon

---

### Post by zaratustra on 2007-02-21
is songbird this? ->
```
DaRkStAr ~ # eix songbird
* media-sound/songbird-bin [1]
     Available versions:  ~0.2.1
     Homepage:            http://www.songbirdnest.com/
     Description:         Songbird is a desktop Web player, a digital jukebox and Web browser mash-up
```

It wants to pull-down gcc-3.3.6-r1 :-O, and it is binary package?!?!
It is compiling now:)

EDIT: FAILED TO COMPILE... enough for me to stop trying to break my system:)

---

### Post by Rodneyck on 2007-02-21
I tried Songbird on Ubuntu and was impressed by its beautiful GUI, but not by the music player itself. It was sort of clunky to me, and it still does not have Amarok beat.

---

### Post by zaratustra on 2007-02-21
I am emulating XP in vmware and I was bored so now I am writing from Songbird for win. Can't say much because I am using it for a few minutes now, but I can say a bit... I don't like things using XUL. I am not a huge fan of N_in_1 things. Maybe a new road is in front of us and maybe this is one of those things which we say "wow" for and remove it in few days:) time will show. Do not forget this is Dev Pre

---

