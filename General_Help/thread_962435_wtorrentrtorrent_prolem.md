---
title: "wtorrent/rtorrent prolem"
date: 2008-10-29
forum: General Help
---

### Post by ikt on 2008-10-29
Hi all,

I have Ubuntu 8.10 installed, I installed rtorrent, apache, the mod for php support, mod_scgi, copied wtorrent over to my /var/www folder, given it the right permissions but I still get this error:

Fatal error: Smarty error: the $compile_dir 'tpl_c/' does not exist, or is not a directory. in /var/www/wtorrent/lib/smarty/Smarty.class.php on line 1092

Searching for it on wtorrent website it says lighttpd doesn't have the right permissions, but I'm not using lighttpd :/

Does anyone have any ideas?:confused:

---

### Post by forger on 2008-10-29
What do you actually need?
A torrent client with web user interface?
Here are some packages with WebUI:
> ktorrent
[deluge-torrent]("http://www.deluge-torrent.org")
transmission (pre-installed with ubuntu hardy heron)


and of course:
> torrentflux - web based, feature-rich BitTorrent download manager - TorrentFlux is a PHP based BitTorrent controller that runs on a web server.

to view more info:
```
apt-cache show yourpackagename
```

to install:
```
sudo apt-get install yourpackagename
```

---

### Post by ikt on 2008-11-02
> **forger said:**
> What do you actually need?
A torrent client with web user interface?
Here are some packages with WebUI:


and of course:


to view more info:
```
apt-cache show yourpackagename
```

to install:
```
sudo apt-get install yourpackagename
```

torrentflux b4rt I've looked at but wtorrent seems a lot better:

[http://www.wtorrent-project.org/trac/screenshots/8?format=html](http://www.wtorrent-project.org/trac/screenshots/8?format=html)

Ideally I'd like to go with it.

I still can't get past the original error in the first post :(

---

### Post by ikt on 2008-11-04
bumpage!~

---

### Post by peppage on 2008-11-07
Did you create the directory "tpl_c/"? and give it the right permissions?  When this happened to me that directory wasn't even there so I just had to use mkdir.

---

### Post by ikt on 2009-02-03
> **peppage said:**
> Did you create the directory "tpl_c/"? and give it the right permissions?  When this happened to me that directory wasn't even there so I just had to use mkdir.

this ended up being what the problem was.

I've got wtorrent fully installed however my issue is now that it won't download/upload.

Any ideas on what I can do?

---

### Post by ikt on 2009-02-03
> **ikt said:**
> this ended up being what the problem was.

I've got wtorrent fully installed however my issue is now that it won't download/upload.

Any ideas on what I can do?

turned out I had the wrong download folder set :/

---

