---
title: "Apache doesn't load webpages after upgrading from 8.10 to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by danking12 on 2009-04-24
Hi,

I upgraded from 8.10 to 9.04 last night and now my Apache doesn't load the webpage I had setup on my computer. I had setup Trac with the subversion repository.

Unfortunately my subversion repository doesn't seem to be working either.

I have no idea what is going on or how to fix it so any help is greatly appreciated.

Thanks

---

### Post by danking12 on 2009-04-24
Here is the apache error log

```
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] mod_python (pid=23592, interpreter='main_interpreter', phase='PythonHandler', handler='trac.web.modpython_frontend'): Application error
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] ServerName: '127.0.1.1'
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] DocumentRoot: '/var/www/'
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] URI: '/projects/supermarker'
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] Location: '/'
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] Directory: None
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] Filename: '/var/www/projects'
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] PathInfo: '/supermarker'
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] Traceback (most recent call last):
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch\n    default=default_handler, arg=req, silent=hlist.silent)
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1202, in _process_target\n    module = import_module(module_name, path=path)
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 304, in import_module\n    return __import__(module_name, {}, {}, ['*'])
[Fri Apr 24 12:22:19 2009] [error] [client 127.0.0.1] ImportError: No module named trac.web.modpython_frontend
dan@chimp:/var/log/apache2$ 

```

---

### Post by hedefalk on 2010-01-11
Did you solve it? I get the same error on 9.10 with a fresh install of trac:

```

[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] mod_python (pid=32481, interpreter='main_interpreter', phase='PythonHandler', handler='trac.web.modpython_frontend'): Application error
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] ServerName: 'xxx'
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] DocumentRoot: '/var/www/'
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] URI: '/projects/'
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] Location: '/projects'
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] Directory: None
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] Filename: '/var/www/projects'
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] PathInfo: '/'
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] Traceback (most recent call last):
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1537, in HandlerDispatch\n    default=default_handler, arg=req, silent=hlist.silent)
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 1202, in _process_target\n    module = import_module(module_name, path=path)
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194]   File "/usr/lib/python2.6/dist-packages/mod_python/importer.py", line 304, in import_module\n    return __import__(module_name, {}, {}, ['*'])
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] ImportError: No module named trac.web.modpython_frontend
[Mon Jan 11 14:27:15 2010] [error] [client 195.252.32.194] File does not exist: /var/www/favicon.ico

```

Trac location:
```
ls -l /usr/local/lib/python2.6/dist-packages
total 240
-rw-r----- 1 root staff    247 2010-01-11 12:58 easy-install.pth
-rw-r----- 1 root root  229942 2010-01-11 12:58 Genshi-0.5.1-py2.6-linux-x86_64.egg
drwxr-sr-- 4 root staff   4096 2010-01-11 12:58 Trac-0.11.6-py2.6.egg
```


Thanks!


/Viktor

---

### Post by danking12 on 2010-01-11
Nope I didn't. I think i just unded up installing everything fresh and starting from scratch. Fortunately this was just something I play with and it wasn't a huge loss.

---

