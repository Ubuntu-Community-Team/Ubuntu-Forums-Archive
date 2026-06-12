---
title: "ktorrent download torrent help"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by kahram.yoon on 2007-11-11
When I try to download torrents, it opens with ktorrent.  The torrents opened do not download.  They stayed stalled.  My internet is working but it will not let me download these torrents.  These torrents definitely have enough seeds to download at least minimally. Any ideas on how to fix this problem?  Btw, I am a total beginner at linux.

---

### Post by rexxxlo on 2007-11-11
im having the exact problem i have tries bittornado azereus and bittorrent with out a gui ewww that is weird

---

### Post by fedex1993 on 2007-11-11
one could be that your ports are not open uped at all or it could be that a certian port is not open either you could try deluge i love deluge. 

```
sudo apt-get install deluge-torrent
```

---

### Post by rexxxlo on 2007-11-11
yup deluge is great i just found it it worked instantly

---

### Post by kahram.yoon on 2007-11-12
deluge doesn't seem to work either.  How do I open these ports?

---

### Post by mexicola on 2007-11-12
Change [Settings - Configure Ktorrent - Downloads - Preferences - Port] to a number between 49152 and 65535.

---

### Post by stimpack on 2007-11-14
If you are behind a router, forward the correct port (6881).
If you are behind a firewall, forward the correct port (6881)

[http://portforward.com/](http://portforward.com/)

---

