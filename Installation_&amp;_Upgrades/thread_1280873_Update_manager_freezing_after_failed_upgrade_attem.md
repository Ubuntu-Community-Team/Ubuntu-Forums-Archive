---
title: "Update manager freezing after failed upgrade attempt"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by ihendley on 2009-10-02
Hi,

I am running Jaunty 64.

Last night I began an upgrade to 9.10, and I left my update manager downloading the required packages for installation, but in the morning I found a message saying that all files could not be downloaded. I think I lost my internet connection at some point overnight.

Now when I run update-manager -d and click on the "Upgrade" button next to "New distribution release '9.10' is available" (which worked successfully the first time I tried to upgrade), the button and window freeze and I have to forcibly exit the program.

Here is the console output:

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 802, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 234, in run
    if not self.showReleaseNotes():
  File "/usr/lib/python2.6/dist-packages/UpdateManager/DistUpgradeFetcher.py", line 63, in showReleaseNotes
    uri = self._expandUri(self.new_dist.releaseNotesURI)
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
The application 'update-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

Does anyone have any idea what the problem is and how I can fix it?

Any help would be greatly appreciated!

---

### Post by Johnny_Lifeson on 2009-10-02
The same thing was happening to me today as well. I believe it's a server issue. Should be ok in a few hours..  I just updated one of my laptops without a problem.

Try again, hope this is of some help..

---

### Post by ihendley on 2009-10-02
> **Johnny_Lifeson said:**
> The same thing was happening to me today as well. I believe it's a server issue. Should be ok in a few hours..  I just updated one of my laptops without a problem.

Try again, hope this is of some help..

Ah, OK. Will try again later. Thanks.

---

