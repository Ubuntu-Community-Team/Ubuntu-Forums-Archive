---
title: "Deluge not connecting to enough seeders"
date: 2008-09-08
forum: General Help
---

### Post by kpkeerthi on 2008-09-08
I fail to understand why deluge (the latest stable) is not connecting to enough seeders. The seeder column is displayed as 20 (2500). So if my understanding is correct, it is connected to only 20 seeders at the moment even though there are 2500 available. My download speed for this torrent is stuck at 20 kBps only.

I checked with another torrent and even though there were only 300 seeders total, deluge connected to about 100 seeders and uses by full download bandwidth.

Does anyone have any idea why in the former case deluge is behaving that way?

**Note: **I only have one torrent actively downloading/seeding at a time.

---

### Post by mb_webguy on 2008-09-08
You said the torrent had 2500 seeds, but how many leeches?  If there are 2500 leeches as well, you're competing with those 2500 other peers for connections with those 2500 seeds.  Except for those people who set their torrent client up as a server, people usually have lower upload limits than for downloads, so each seed probably only allows a handful of simultaneous connections for uploading.  If there is a large number of leeches, you'll be able to connect to fewer seeds.

Also, there's the issue of how many simultaneous connections your client can have.  By default, the most recent version of Deluge has all network settings at unlimited, which makes it a real bandwidth hog.  If you've lowered these settings (which you probably should, especially if you're behind a router) then you're subject to those limitations.

---

### Post by kpkeerthi on 2008-09-08
> **mb_webguy said:**
> You said the torrent had 2500 seeds, **but how many leeches?  If there are 2500 leeches as well, you're competing with those 2500 other peers for connections with those 2500 seeds.**  Except for those people who set their torrent client up as a server, people usually have lower upload limits than for downloads, so each seed probably only allows a handful of simultaneous connections for uploading.  If there is a large number of leeches, you'll be able to connect to fewer seeds.

Also, there's the issue of how many simultaneous connections your client can have.  By default, the most recent version of Deluge has all network settings at unlimited, which makes it a real bandwidth hog.  If you've lowered these settings (which you probably should, especially if you're behind a router) then you're subject to those limitations.

Thanks for the insight. There were way too many leechers (5000+) when I last checked. So all those leechers are hitting hard on the generous 2500 seeders leaving only 20 for me. Not good leachers!.
 
Great, I was bitching Deluge. Feel stupid about it. Now I understood why the other torrent was faster despite only 300 seeders (because it had virtually no leechers). Thanks for your help.

---

### Post by mb_webguy on 2008-09-08
Yeah, when downloading torrents, a lot of people think that if there are a lot of seeds then the download will be faster, but really it's the seed/leech ratio.  More seeds means a more reliable download, and a *potentially* faster download since there's a higher chance that some of the seeds will have very fast upload speeds.  But what you're really looking for, as far as speed is concerned, is a high seed/leech ratio.  As long as it's 1:1 or better, you should get pretty good download speeds, but if it gets around 1:2 or lower, it's going to be slow no matter how many seeds there are.

On the other hand, a large number of leeches can be a good thing, too, since you're also grabbing pieces of the torrent from them.  The torrent you're talking about, with 2500 seeds and 5000 leeches, could still offer good download speeds as long as your peers (the other leeches) have the bits of the torrent you don't.

---

### Post by kpkeerthi on 2008-09-08
> **mb_webguy said:**
> Yeah, when downloading torrents, a lot of people think that if there are a lot of seeds then the download will be faster, but really it's the seed/leech ratio.  More seeds means a more reliable download, and a *potentially* faster download since there's a higher chance that some of the seeds will have very fast upload speeds.  But what you're really looking for, as far as speed is concerned, is a high seed/leech ratio.  As long as it's 1:1 or better, you should get pretty good download speeds, but if it gets around 1:2 or lower, it's going to be slow no matter how many seeds there are.

On the other hand, a large number of leeches can be a good thing, too, since you're also grabbing pieces of the torrent from them.  The torrent you're talking about, with 2500 seeds and 5000 leeches, could still offer good download speeds as long as your peers (the other leeches) have the bits of the torrent you don't.

Exactly. Thanks again.

---

