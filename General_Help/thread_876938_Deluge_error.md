---
title: "Deluge error"
date: 2008-08-01
forum: General Help
---

### Post by graabein on 2008-08-01
Hi, I tried searching but did not find any info on this. I can't start Deluge. I get this traceback:

```
**$ deluge **
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin WebUi
Initialising plugin TorrentPeers
Initialising plugin DesiredRatio
Initialising plugin MoveTorrent
Initialising plugin TorrentCreator
Initialising plugin NetworkHealth
Initialising plugin BlocklistImport
Initialising plugin TorrentNotification
Initialising plugin Scheduler
Initialising plugin EventLogging
Initialising plugin NetworkGraph
Initialising plugin SpeedLimiter
Initialising plugin Search
Initialising plugin FlexRSS
Initialising plugin WebSeed
Initialising plugin TorrentFiles
Applying preferences
Starting DHT...
Showing window
Traceback (most recent call last):
  File "/usr/bin/deluge", line 133, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 117, in start_deluge
    interface.start(get_cmd_line_torrents())
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1029, in start
    self.update()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1208, in update
    self.update_torrent_info_widget()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 1282, in update_torrent_info_widget
    self.tab_details.update(unique_id)
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 173, in update
    self.paint_customprogress()
  File "/var/lib/python-support/python2.5/deluge/tab_details.py", line 82, in paint_customprogress
    gc = progress_window.new_gc()
AttributeError: 'NoneType' object has no attribute 'new_gc'
**$**
```

---

### Post by Choad on 2008-08-01
which version of deluge are you using? the one in the repositories is horribly out of date

---

### Post by graabein on 2008-08-05
Good idea. :) 

I installed it from their [website]("http://deluge-torrent.org/") and it started up okay but my previous torrents where not to be seen. I had to remove the previous version to get it to install (some conflict over **deluge-torrent-common**) so maybe my torrents was lost at the same time. It's weird though, cause config and userdata usually is kept after removal. 

:confused:


Is that a picture of Cat Power Chan Marshall btw? I used to be quite into her.

---

### Post by Choad on 2008-08-06
lulz, no it is me. i guess i can see a similarity tho. maybe...

[http://media.collegepublisher.com/media/paper871/stills/3b7c22a822fe1-83-1.jpg](http://media.collegepublisher.com/media/paper871/stills/3b7c22a822fe1-83-1.jpg)

---

