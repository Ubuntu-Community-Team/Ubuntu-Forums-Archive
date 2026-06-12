---
title: "Ktorrent, almost all peers are 'choked'"
date: 2008-10-08
forum: General Help
---

### Post by malfist on 2008-10-08
Hello, I"ve been trying to download some things using Ktorrent, and I've been using bit torrents for a long time, but I can't seem to figure this one out.
I have this torrent with nearly 300 seeders and a similar number of leachers, I should be able to download that pretty fast correct? So far I've not seen over 10 kB/s in several days. This would normally be a few hour download. When I check on the peers, it tells me that most of them are 'choked', does anyone know how to fix this? I'm behind a firewall I have no control over, but I know port 8080 is open, however when I tell KTorrent to use that port, it can't seem to.

---

### Post by Archmage on 2008-10-08
Choked means that the client things that you haven't uploaded enough and therefore give to other clients that have given them more.

---

### Post by malfist on 2008-10-08
What? I have my upload unrestricted, and this problem also applies to my upload speeds too, I just used my download speed as an example.

I can be one of seven seeds with 20-30 leechers and have 3 leechers connected to me and I'm not uploading anything.

My share ratio is set to stop after 5 and I usually let it go until then. I have an throttled upload speed too. I can easily upload 500KB/s and probably more. I know my speed tests I've taken say I can upload 7503KB/s and 10.3 MB/s down.

---

### Post by Archmage on 2008-10-09
Than either your uploadspeed is to high (try it with 11 and see if the problem presist), your router or something can't handle that much connections (try to limit your connections) or your ISP is throttling you (try to clock your traffic).

---

### Post by malfist on 2008-10-10
My ISP is the university and the traffic is encrypted. I switched to deluge and it worked a whole lot better. It must be a configuration issue with Ktorrent. Maybe I'll try and purge the config and reinstall. Or I'll just stick with deluge.

Malfist

---

### Post by BigBananaMan on 2009-12-15
I'm having the same problem.  Just downloaded Ubuntu 9.10 i386.  I am connected to 12 of 287 leeches and none of them (many at 0%) are interested in downloading from me, all choked.  It must have something to do with there being 2698 seeders.  When I seed at around 6k, they just find other seeds to be faster and choke me so I'm not worried.  That just means a lot of other people out there are helping and I can end seeding prematurely.  Check how many seeds there are and if your situation is similar to mine, you're fine.

---

### Post by Kanedagr on 2010-10-19
The exact same problem with the above mentioned. I am downloading something (the speed depending on the seeders), and then when i am reaching 100% and i let it seed to keep my ratio good, it stops and do nothing. When i press Manual Announce it displays some leechers and then they disappear. I moved from deluge cause of the stop button that ktorrent has and deluge don't. But what is this with that problem? Very strange!!

---

### Post by NennokraH on 2011-02-28
Hi all,

I have the same problem with the Ktorrent client only. I even switched to Kubuntu from Ubuntu to see of there is a QT problem but it seems it would not upload anything. It's obviously a problem of setting Ktorrent correctly but what are the settings. I am not new to torrents and this is the only client I am having problem with but I like the possible features in it so I want to use this one

---

