---
title: "[SOLVED] rtorrent doanload disappears after restarting app"
date: 2008-07-12
forum: General Help
---

### Post by kaivalagi on 2008-07-12
I wonder if someone can help...

I have setup rtorrent (along with rtgui in apache) and it works just fine when fired up in a terminal session as follows:

```
gnome-terminal -x rtorrent
```

I can add a bittorrent through rtgui for download and it starts no problem, files are created and the download commences, and I can even see the status through my local web server. At this point everything looks just great :)

The problem I have is that if I kill rtorrent (even after stopping the torrent) and start it again, the torrent is no longer there in the list?

Can anyone explain why this might be happening? I would assume rtorrent doesn't just keep a torrent registered for the life of it's current process? Am I missing the point with something?

I've attached my .rtorrent.rc file in case that may have something to do with it...

Any help is very much appreciated

---

### Post by kaivalagi on 2008-07-12
Fixed up the issue myself....10 minutes after I posted the question :oops:

I didn't setup the session path in the rc file...I can quit or kill rtorrent, when started again everything is as was...

---

