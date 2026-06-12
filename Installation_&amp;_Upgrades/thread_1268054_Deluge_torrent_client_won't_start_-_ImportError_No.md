---
title: "Deluge torrent client won't start - ImportError: No module named libtorrent"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by omfgbunnies on 2009-09-16
Running deluged gives me this error:

```
# cat deluged.log 
[ERROR   ] 18:06:25 main:207 No module named libtorrent
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/deluge/main.py", line 204, in start_daemon
    Daemon(options, args)
  File "/var/lib/python-support/python2.5/deluge/core/daemon.py", line 54, in __init__
    from deluge.core.core import Core
  File "/var/lib/python-support/python2.5/deluge/core/core.py", line 57, in <module>
    import libtorrent as lt
ImportError: No module named libtorrent

```


Basically this happens when I attempt to launch deluged. I'm assuming this is the reason that I'm getting this error in the webui:

```
--Deluge Error--
NoCoreError : 'The core proxy is invalid.'
path : /connect
file : /var/lib/python-support/python2.5/deluge/ui/client.py in call, line 123

--Input--
<Storage {'other_uri': '', 'uri': 'http://localhost:58846', 'submit': 'Connect'}>

--Versions--
WebUi : 1.1.9r
Python 2.5.3 (r253:67855, Dec 21 2008, 10:45:24) 
[GCC 4.3.3 20081217 (prerelease)]:

--Traceback--
  File "/var/lib/python-support/python2.5/deluge/ui/webui/lib/webpy022/webapi.py", line 310, in wsgifunc
    result = func()
  File "/var/lib/python-support/python2.5/deluge/ui/webui/lib/webpy022/request.py", line 131, in <lambda>
    func = lambda: handle(inp, fvars)
  File "/var/lib/python-support/python2.5/deluge/ui/webui/lib/webpy022/request.py", line 61, in handle
    return tocall(*([x and urllib.unquote(x) for x in args] + fna))
  File "/var/lib/python-support/python2.5/deluge/ui/webui/pages.py", line 334, in POST
    utils.daemon_connect(uri)
  File "/var/lib/python-support/python2.5/deluge/ui/webui/utils.py", line 211, in daemon_connect
    webui_plugin_manager.start()
  File "/var/lib/python-support/python2.5/deluge/ui/webui/components.py", line 151, in start
    aclient.get_enabled_plugins(self._on_get_enabled_plugins)
  File "/var/lib/python-support/python2.5/deluge/ui/client.py", line 377, in async_proxy
    return self.core.call(method_name, *args, **kwargs)
  File "/var/lib/python-support/python2.5/deluge/ui/client.py", line 124, in call
    raise deluge.error.NoCoreError("The core proxy is invalid.")

```

I seem to have libtorrent on the system:
```
# apt-get install python-libtorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-libtorrent is already the newest version.
```


What can I do to make deluged start?  :oops:

---

