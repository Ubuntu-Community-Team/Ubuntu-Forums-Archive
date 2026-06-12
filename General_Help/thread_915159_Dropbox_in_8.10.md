---
title: "Dropbox in 8.10"
date: 2008-09-09
forum: General Help
---

### Post by kalbir on 2008-09-09
Hi All,

My dropbox client is not connecting [Dropbox is a cross computer/online backup system, check here: [http://getdropbox.com]](http://getdropbox.com]) . I am running Ubuntu 8.10. I installed it using the repos method and killed nautilus etc. When I run nautilus in the terminal I get the following:

XXX@desktop:~$ killall nautilus
nautilus: no process killed
XXX@desktop:~$ nautilus
Initializing nautilus-share extension
Initializing nautilus-dropbox 0.4.0

** (nautilus:14778): WARNING **: Unable to add monitor: Not supported
dropboxd: no process killed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Traceback (most recent call last):
File "<string>", line 6, in <module>
File "__main__.py", line 105, in <module>
File "__main__dropbox__.py", line 174, in <module>
File "__main__dropbox__.py", line 169, in main_startup
File "arch/linux/startup.py", line 129, in main_thread_loop
File "ui/wx_core.py", line 4, in <module>
File "wx/__init__.py", line 45, in <module>
File "wx/_core.py", line 4, in <module>
File "wx/_core_.py", line 14, in <module>
ImportError: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: cairo_has_current_point
dropboxd: no process killed
Traceback (most recent call last):
File "<string>", line 6, in <module>
File "__main__.py", line 105, in <module>
File "__main__dropbox__.py", line 174, in <module>
File "__main__dropbox__.py", line 169, in main_startup
File "arch/linux/startup.py", line 129, in main_thread_loop
File "ui/wx_core.py", line 4, in <module>
File "wx/__init__.py", line 45, in <module>
File "wx/_core.py", line 4, in <module>
File "wx/_core_.py", line 14, in <module>
ImportError: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: cairo_has_current_point
Exception in thread AUTHENTICATE (most likely raised during interpreter shutdown):
Traceback (most recent call last):
File "threading.py", line 486, in __bootstrap_inner
File "client_api/authenticate.py", line 203, in run
File "common_util/trace.py", line 468, in unhandled_exc_handler
Exception in thread RTRACE (most likely raised during interpreter shutdown):
Traceback (most recent call last):
File "threading.py", line 486, in __bootstrap_inner
File "common_util/trace.py", line 486, in run
File "common_util/trace.py", line 412, in rtrace_thread_func
<type 'exceptions.TypeError'>: 'NoneType' object is not callable
Unhandled exception in thread started by
Error in sys.excepthook:

Original exception was:
<type 'exceptions.TypeError'>: 'NoneType' object is not callable
Unhandled exception in thread started by
Error in sys.excepthook:

Original exception was:

It hangs on that final line and the icon in the systray says "reconnecting to dropbox". Any ideas?

Many thanks in advance,

Kalbir

---

### Post by vkkim on 2009-01-12
Same issue:

```
victor@victor-desktop ~ $ nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.5.0

** (nautilus:10432): WARNING **: Unable to add monitor: &#51648;&#50896;&#46104;&#51648; &#50506;&#51020;
dropboxd: no process killed
Traceback (most recent call last):
  File "<string>", line 6, in <module>
  File "__main__.py", line 105, in <module>
  File "__main__dropbox__.py", line 2, in <module>
  File "arch/__init__.py", line 17, in <module>
  File "core/preferences.py", line 226, in <module>
  File "core/preferences.py", line 133, in read
  File "core/client_model.py", line 188, in wrapped
  File "common_util/achub.py", line 24, in __enter__
  File "common_util/achub.py", line 95, in begin
  File "sqlobject/dbconnection.py", line 358, in transaction
  File "sqlobject/dbconnection.py", line 746, in __init__
  File "sqlobject/sqlite/sqliteconnection.py", line 119, in getConnection
  File "sqlobject/sqlite/sqliteconnection.py", line 163, in makeConnection
sqlite3.OperationalError: unable to open database file

```

---

### Post by csmth on 2009-01-20
I have removing .dropbox and .dropbox-dist, reinstalling the deb and no luck. But I found a workaround for this problem.

At "Almost Text-based Install":
[http://wiki.getdropbox.com/TipsAndTricks/AlmostText-BasedLinuxInstall](http://wiki.getdropbox.com/TipsAndTricks/AlmostText-BasedLinuxInstall)

I follow the steps and can use the Pthyon script to start the dropbox. I realized that correct (workable) for my x86_64 .dropbox-dist should be "dropbox-lnx.x86_64-0.6.416.tar.gz". I have tried 0.6.427 and 0.6.432 and they are no good.

---

