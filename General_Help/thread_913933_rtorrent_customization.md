---
title: "rtorrent customization"
date: 2008-09-08
forum: General Help
---

### Post by ains on 2008-09-08
Hi all.

For some reason, I can't get rtorrent to automatically start new torrents despite changing .rtorrent.rc

I copied the default .rtorrent.rc to /home, then

```
sudo gedit .rtorrent.rc
```

I removed the hash next to 'Watch a directory ..' so it is as follows:

```
schedule = watch_directory,5,5,load_start=/home/ains/Downloads/*.torrent
```

Is there anything else I need to do? rtorrent doesn't automatically find the new torrents when they're placed there.

Also, is there anyway to set rtorrent up to automatically load previous unfinished torrents rather than doing it manually every time?

Sorry if this is something very simple! Still trying to learn :)

Thanks in advance..

---

### Post by Sycron on 2008-09-08
I have not used rtorrent but Transmission BitTorrent Client was doing that automatically.

---

### Post by ains on 2008-09-08
> **Sycron said:**
> I have not used rtorrent but Transmission BitTorrent Client was doing that automatically.

I'm using rtorrent because I have a very old computer running a minimal install and rtorrent is just great. 

Hope someone can help :)

---

