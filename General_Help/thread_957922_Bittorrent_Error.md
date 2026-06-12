---
title: "Bittorrent Error"
date: 2008-10-24
forum: General Help
---

### Post by Western Digital on 2008-10-24
I get that consistently (about every 8 seconds) when downloading a torrent. The torrent downloads with normal speeds, I just don't know what to make of this error.

Thanks

```
|          [16:20:23] Message parsing failed                                                                                                                                    |
|          [16:20:23] Traceback (most recent call last):                                                                                                                        |
|          [16:20:23]    File "/usr/lib/python2.4/site-packages/BitTorrent/Connector.py", line 966, in data_came_in                                                             |
|          [16:20:23]    File "/usr/lib/python2.4/site-packages/BitTorrent/Connector.py", line 658, in _read_messages                                                           |
|          [16:20:23]    File "/usr/lib/python2.4/site-packages/BitTorrent/Connector.py", line 713, in _got_message                                                             |
|          [16:20:23]    File "/usr/lib/python2.4/site-packages/BitTorrent/Connector.py", line 669, in _got_utorrent_msg                                                        |
|          [16:20:23]  exceptions.TypeError: iterable argument required       
```

---

### Post by Western Digital on 2008-10-24
Bump

---

