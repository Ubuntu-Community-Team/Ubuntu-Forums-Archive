---
title: "Transmission takes very long time to download anything"
date: 2008-10-02
forum: General Help
---

### Post by rapolas on 2008-10-02
It may sound as my internet slow, but its not. For example 700mb file takes about 12h to download, and my internet speed is 4mbit/s, so it should take about 30-40minutes to do it. It's just downloading something, the speed is right, the time it shows to complete also right. I mean that transmission shows, that it is downloading at normal speed, the total download increasing I think also normally, but actual file is not.

---

### Post by russlar on 2008-10-02
Transmission is a bittorrent client, your download speed is governed by the upload speed of those seeding the file.

---

### Post by jerome1232 on 2008-10-02
Well with torrenting there are ALOT of variables to be considered.

Like how many seeders vs leechers are there for your particular torrent?
Do you have port 51413 open? (that's the default transmission port)?

If you have alot of seeders and few leechers, you will get good speeds.
If that port is closed transmission will get slow speeds so make sure it is forwarded in your router and such.

---

### Post by rapolas on 2008-10-02
I understand all that, and I'm saying that both system monitor and transmission itself shows me, that download is at the highest speed my isp gives me. I mean the actual transfer, not only settings. And also if I open torrent details, the estimated time shows correct time. Just if I open the same's torrent details again after ten minutes, it's estimated time is only minute lower..

---

### Post by Ryadt on 2008-10-02
Why not use another client. 
Deluge works great for me. It's in the repos.

---

### Post by jerome1232 on 2008-10-02
Ah, I misinterpreted your OP

Wierd, and does it actually take a long time to download? 

Does the transmission rate stay consistent or does it bounce around, or drop?

Might want to try another torrent client like deluge it's in the repos see if you get the same results. That way we can determine if it's transmission that's screwing up or not.

---

### Post by rapolas on 2008-10-02
> **Ryadt said:**
> Why not use another client. 
Deluge works great for me. It's in the repos.

I'm thinking to do that, just I'm used to transmission :) I'll try to delete old configurations, all torrents files, just to be sure, that it is not some problems with configuration or updating from old version without uninstalling issues.

---

### Post by rapolas on 2008-10-02
Nop, it didn't help. Lets see what deluge can offer;)

Jerome1232, yes it actually takes very long time to download a bigger file. Rate stays consistent, the thing is, where transmission has its total download/upload or session download/upload, I think that shows correctly how much data transfered (or only how much data should be transfered). When I open torrent details I see much less downloaded. I just tried completely fresh install, after deleting everything related to it. And now trying deluge, this seems to work nice.

---

