---
title: "[SOLVED] Quit GUI apps with PuTTY"
date: 2008-07-18
forum: General Help
---

### Post by masterdam79 on 2008-07-18
Hi,

I'm looking to find a way to quit (not kill) any Application running on my Ubuntu Desktop (e.g. Firefox) remotely.

I'm fairly new to Ubuntu Linux so I think there myst be an easy way to do this like ```
/usr/bin/firefox stop
``` or something.

More specifically I'm running rtorrent on the machine but can't administrate it remotely if it is already running (something to do with sessions).
So I want to remotely close the application (which is running on the Ubuntu Desktop in a Terminal venster) and re-open rtorrent in PuTTY on my work to see how far my torrents are or maybe add a few more.

I've tried to kill the app remotely through ```
ps ux | grep rtorrent
``` and then ```
kill -9 #####
``` with the PID I got from ```
ps ux
```.
This resulted unfortunately in losing my session and having to re-load all torrents from 0%.

I just want to (remotely) say "Quit rtorrent on local machine" and "Start rtorrent again in PuTTY" so it terminated the connections to the trackers properly and saves the session.

There must be a way....

TY:neutral:

---

### Post by bodhi.zazen on 2008-07-18
Well, not exactly what you are asking, but you could try screen and rtorrent.

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

See also : [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Savingtorrentstateandresumedatabetweensessions](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Savingtorrentstateandresumedatabetweensessions)

Otherwise, I think you will need to kill.

You can try (progressively)

kill `pidof <command>`

pkill command

kill -9 `pidof <command>`

---

### Post by masterdam79 on 2008-07-20
> **bodhi.zazen said:**
> Well, not exactly what you are asking, but you could try screen and rtorrent.

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

See also : [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Savingtorrentstateandresumedatabetweensessions](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Savingtorrentstateandresumedatabetweensessions)

Otherwise, I think you will need to kill.

You can try (progressively)

kill `pidof <command>`

pkill command

kill -9 `pidof <command>`
Hey Thanks Bohdi,

I had to look into it for a bit, but screen is very handy indeed!!
Thanks heaps!!

Richard

---

