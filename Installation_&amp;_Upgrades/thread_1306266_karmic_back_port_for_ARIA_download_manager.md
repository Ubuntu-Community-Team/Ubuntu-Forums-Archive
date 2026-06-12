---
title: "karmic back port for ARIA download manager"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by str0g on 2009-10-30
Hello

I would like to use this awesome download manager under karmic but I need to back-port some how:
libglib1.2ldbl (>= 1.2.10-18 )
libgtk-1.2.so.0

link to latest deb package and source
[https://launchpad.net/ubuntu/+source/aria/1.0.0-17](https://launchpad.net/ubuntu/+source/aria/1.0.0-17)

Please don't tell me that there are download managers in repo they are so f**** crappy that I faster jump out from the window then use them.
I wish someone tell me how to do it or just do it for me thanks for attention :-)

well it was easer the I exacted but it cost me a lot of time here's link for x64 systems(contains aria_1.0.0-16.1 aria_1.0.0-17 libglib1.2ldbl libgtk-1.2 libgtk-1.2-common)

[http://rapidshare.com/files/300062645/aria_1.0.0-17_amd64.rar](http://rapidshare.com/files/300062645/aria_1.0.0-17_amd64.rar)

---

### Post by foxmulder881 on 2009-12-28
Actually I'm curious also as to why Aria was not followed on to Karmic.

It's definitely the best gui download tool I've ever used.

---

### Post by Linuxforall on 2009-12-28
Have you tried Multiget, its an excellent downloader as well with very nice GUI and is in the repo.

---

### Post by foxmulder881 on 2009-12-28
Actually no I haven't and I won't be as I have just finished manually installing Aria. Manually sourced the required dependencies due to me running i386 and not x64. Installed the required deps using dpkg and then installed the final aria package with gdebi. All running perfect! :)

I'll upload the package archive and post link for anyone else wanting to do the same for i386 architecture.

Rapidshare link:
```
http://rapidshare.com/files/327312191/aria_1.0.0i386.rar
```

---

### Post by moresun on 2010-01-16
Thanks foxmulder881 

You saved my day, because aria is the only download manager which is able to store rapidshare passwords.

It your installation works perfect.

[http://rapidshare.com/files/327312191/aria_1.0.0i386.rar](http://rapidshare.com/files/327312191/aria_1.0.0i386.rar)

Greetings

---

### Post by foxmulder881 on 2010-01-16
Glad I could help mate. It's still one of my favorite download managers of all time.

---

### Post by Eggbanjo on 2010-01-22
Cheers for this, its a life saver.

---

### Post by iceman_ca on 2010-01-31
Thanks for the 64bit package. I missed not having the best downloader in linux up and running. 
Ubuntu please see fit in making this package available in the future. It was sorely missed by quite a few of us.

---

### Post by foxmulder881 on 2010-02-28
I'm glad my links have been able to have helped quite a few people so far. ;)

---

### Post by madjr on 2010-05-08
thanks guys

this is also working in lucid

best download manager, too bad is not in the repos

---

### Post by unicag on 2010-05-14
Thanks for the files.
I tried some download managers but Aria is the best.
I use it for Rapidshare downloads.

---

### Post by madjr on 2010-05-14
well another download manager that works really well is **[FatRat]("http://fatrat.dolezel.info/screenshots")** (is in the repos)

it simply works, you can change the speed on the fly, has download basket, active dev, even support torrents (haven't tried this yet), etc.


Features of the Git version:

    * HTTP(S)/FTP/SFTP downloads
    * FTP/SFTP uploads
    * RSS feed support + special functions for TV shows and podcasts
    * BitTorrent support (including torrent creating, DHT, UPnP, encryption etc.)
    * Torrent search
    * Support for SOCKS5 and HTTP proxies
    * RapidShare.com FREE downloads
    * RapidShare.com uploads
    * RapidShare.com link verification and folder extraction
    * RapidSafe link decoding
    * MD4/MD5/SHA1 hash computing
    * Remote control via Jabber (!)
    * Remote control via a web interface
    * YouTube video downloading

And even more is available thanks to the plugins.



for me is second best to aria, the only feature i feel lacking is integration with flashgot, which am going to check out with the devs :)

---

### Post by foxmulder881 on 2010-05-14
FatRat screenshots look pretty sleek. Personally, I've since implemented a home server to handle all my downloads and torrents. So I no longer use a download manager on Ubuntu.

---

### Post by badger on 2010-05-29
Thanks for this, aria1 "just works", the inbuilt timer makes it easy for me to use my ISP's off-peak data allowance. Yes cron can be used for the same, but aria1 makes it simple to override the timer.

---

### Post by windquest on 2010-06-09
Just a note to say thanks for the rapidshare link.. works great. Aria is by far the easiest Gui for timed downloads and bulk files.

---

