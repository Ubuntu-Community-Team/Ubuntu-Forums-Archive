---
title: "update-manager does not start dist-upgrade tool"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by JeroenBaten on 2009-11-06
Hello,

When I start the update-manager and click on the "upgrade" button nothing happens and after some seconds the window grays out and after some minutes of no activity I ctrl-C the thing.

I am behind a MS proxy, but normale package update works fine using ntlmapp or proxy settings.

after setting al debug options in apt.conf this is the output:
Garbage: lvm2
Garbage: python-gtk-vnc
Garbage: watershed
Garbage: python-urlgrabber
** Pass A
** Pass B
** Pass C
** Pass D
** Unpack ordering done





^CTraceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 802, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 234, in run
    if not self.showReleaseNotes():
  File "/usr/lib/python2.6/dist-packages/UpdateManager/DistUpgradeFetcher.py", line 63, in showReleaseNotes
    uri = self._expandUri(self.new_dist.releaseNotesURI)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 187, in _expandUri
    if not url_downloadable(new_uri, self._debug):
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
root@jeroen-desktop:/etc/apt# 

anyone a clue?

---

