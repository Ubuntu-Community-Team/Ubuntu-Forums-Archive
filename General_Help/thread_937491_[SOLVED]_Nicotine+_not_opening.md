---
title: "[SOLVED] Nicotine+ not opening"
date: 2008-10-03
forum: General Help
---

### Post by iflanery on 2008-10-03
Ever since I upgraded to Hardy Heron, Nicotine+ has been crashing on me left and right. The situation came to a head today as Nicotine+ froze up at random--as it does everyday or so. So I performed an xkill, as I typically do in this situation. The only problem is that Nicotine+ hasn't opened since. Logging out and back in didn't work, restarting didn't work, uninstalling and reinstalling Nicotine+ didn't work.... I'm positively stumped.

Is there any way I can get Nicotine+ to boot back up, or am I pretty much out of luck?

---

### Post by Bakon Jarser on 2008-10-03
Did you check 'mark for complete removal' when you uninstalled nicotine+?  If not, it left the configuration files behind in your home folder under .nicotine.  Also, make sure you are using the latest version of nictone+ 1.2.9

---

### Post by iflanery on 2008-10-10
Sorry for the delay. Anyway, I went into GNOME, into Synaptic, marked for complete removal, and just now installed the latest version of Nicotine+ from the Debian website. The problem remains.

---

### Post by Yellow Pasque on 2008-10-11
Try to open the program from a terminal. Does it produce any error messages?

---

### Post by iflanery on 2008-10-11
Yup, in fact it does.

> Traceback (most recent call last):
  File "/usr/bin/nicotine", line 195, in <module>
    app = frame.MainApp(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 2692, in __init__
    self.frame = NicotineFrame(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 133, in __init__
    self.np = NetworkEventProcessor(self, self.callback, self.logMessage, self.SetStatusText, config)
  File "/var/lib/python-support/python2.5/pynicotine/pynicotine.py", line 123, in __init__
    self.CompressShares("normal")
  File "/var/lib/python-support/python2.5/pynicotine/pynicotine.py", line 423, in CompressShares
    m.makeNetworkMessage(nozlib=0, rebuild=True)
  File "/var/lib/python-support/python2.5/pynicotine/slskmessages.py", line 1196, in makeNetworkMessage
    msg = msg + self.packObject(len(self.list.keys()))
  File "/usr/lib/python2.5/shelve.py", line 92, in keys
    return self.dict.keys()
  File "/usr/lib/python2.5/bsddb/__init__.py", line 252, in keys
    return _DeadlockWrap(self.db.keys)
  File "/usr/lib/python2.5/bsddb/dbutils.py", line 62, in DeadlockWrap
    return function(*_args, **_kwargs)
bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')

---

### Post by Yellow Pasque on 2008-10-11
You should include that output in your bug report [http://www.nicotine-plus.org/newticket](http://www.nicotine-plus.org/newticket)

---

### Post by iflanery on 2008-12-18
Problem solved. All I had to do was delete the config files from my ~/.nicotine directory and that got it working again.

---

