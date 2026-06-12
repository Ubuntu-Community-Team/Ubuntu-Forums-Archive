---
title: "update manager freezes"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by damogran on 2009-10-29
Hi there,

i'm just trying to upgrade to karmic, but when i hit the upgrade button in the update-manger nothing happens. the application freezes after some seconds.

i wish i could provide more details, but dont have any output, logs or something like that.

apt-get updates and upgrades works great, no problem here.

---

### Post by damogran on 2009-10-29
same problem when i try using do-release upgrade

$ sudo do-release-upgrade -m desktop
Checking for a new ubuntu release

then, nothing happens


$ ps auxww | grep upgrade
root     19598  0.3  0.2  26292 13632 pts/1    S+   19:29   0:00 /usr/bin/python2.6 /usr/bin/do-release-upgrade -m desktop

---

### Post by damogran on 2009-10-29
that sucks, no disk IO, no network IO
nothing 

just a windowmanger that tells me my window is not responding....

---

### Post by r0t on 2009-10-29
My GUI freezes, then tells me "Could not donwload the release notes, please check internet connection", or something like that. Could it just be that the ubuntu servers are overloaded atm?

---

### Post by Magic_Spehar on 2009-10-29
same here ...

---

### Post by damogran on 2009-10-29
i wish my gui would tell me anything. :))

---

### Post by Magic_Spehar on 2009-10-29
It's a server issue.  My problem was resolved by going to System-Administration-Software Sources.  Then choose download from Main Server.  I was using a local server. 

Now my upgrade manager is working fine.

---

### Post by damogran on 2009-10-30
> **Magic_Spehar said:**
> It's a server issue.  My problem was resolved by going to System-Administration-Software Sources.  Then choose download from Main Server.  I was using a local server. 

Now my upgrade manager is working fine.


Works for me.

But sorry, there should be a way to inform the user about the server load. but a freezing window isn't really helpful. 


thanks magic_spehar

---

### Post by pchev on 2009-10-30
Same problem for me, thank you for the hint because I was wrongly searching for a proxy problem. I change for main server and my upgrade is now running.
I try a few other European server but none work, only the main server archive.ubuntu.com work.

Here a trace it do after hitting ^C after waiting for a while in do-release-upgrade: 

# do-release-upgrade
Checking for a new ubuntu release
^CTraceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 61, in <module>
    fetcher.run()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 236, in run
    if not self.fetchDistUpgrader():
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 203, in fetchDistUpgrader
    uri = self._expandUri(self.new_dist.upgradeToolSig)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in _expandUri
    new_uri = self.mirror_from_sources_list(uri, self.DEFAULT_MIRROR)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 164, in mirror_from_sources_list
    if url_downloadable(mirror_uri, self._debug):
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/utils.py", line 77, in url_downloadable
    c.request("HEAD", path)
  File "/usr/lib/python2.6/httplib.py", line 874, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python2.6/httplib.py", line 911, in _send_request
    self.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 868, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 740, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 683, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 505, in create_connection
    sock.connect(sa)
  File "<string>", line 1, in connect
KeyboardInterrupt

---

### Post by bashphoenux on 2009-10-30
press alt+f2

type update-manager -d !!

---

### Post by pchev on 2009-10-30
"update-manager -d" do exactly the same, it not display anything and seem locked, pressing ^C show the same trace.
I initially try do-release-upgrade with the hope to get more console message because update-manager do not work.

This may be finally proxy related because I try from home without proxy on a computer with a similar setup and it work like a charm.

The computer with the problem was at work behind a crappy MS proxy. But if this is a proxy problem why it work with archive.ubuntu.com and not with de.archive.ubuntu.com ?

---

### Post by Spccowboy on 2009-10-30
Changing the source to main server fixed my problem as well. Previously it was either freezing entirely or say that it could not download the release notes.

---

### Post by tin2001 on 2009-11-11
Changing the software source to Main worked for me too... Seems to be a combination of proxy+odd servers. Or possibly a broken parent proxy in my case sending bad redirects about expired passwords.

---

