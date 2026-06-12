---
title: "miro won't work or install in 9.04"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by fishtoprecords on 2009-06-03
I've been using Miro for a long time. I just upgraded to 9.04 without any major issues. But miro won't run.
So I uninstalled it, and tried again.

I even did a 'locate miro' and removed all the files everywhere.

Then I reinstalled it using synaptic.

When I run it from the shell, it complains about some python libraries, and fails.
> 
pfarrell@tools:~$ miro
/var/lib/python-support/python2.6/miro/util.py:38: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 46, in <module>
    import miro.feedparser
  File "/var/lib/python-support/python2.6/miro/feedparser.py", line 51, in <module>
    (config.get(prefs.SHORT_APP_NAME),
  File "/var/lib/python-support/python2.6/miro/config.py", line 90, in get
    __checkValidity()
  File "/var/lib/python-support/python2.6/miro/config.py", line 122, in __checkValidity
    load()
  File "/var/lib/python-support/python2.6/miro/config.py", line 66, in load
    app.configfile = AppConfig(theme)
  File "/var/lib/python-support/python2.6/miro/appconfig.py", line 48, in __init__
    self.default_vars = util.read_simple_config_file(app_config_path)
  File "/var/lib/python-support/python2.6/miro/util.py", line 100, in read_simple_config_file
    f = open(path, "rt")
IOError: [Errno 2] No such file or directory: '/usr/share/miro/resources/app.config'


---

### Post by fishtoprecords on 2009-06-04
I uninstalled it, and did a 
apt-get update

and reinstall it. Seems to be working. Not sure what the cause was.

---

