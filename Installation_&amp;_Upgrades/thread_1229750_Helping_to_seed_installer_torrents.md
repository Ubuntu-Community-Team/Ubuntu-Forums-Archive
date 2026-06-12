---
title: "Helping to seed installer torrents"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by skullmunky on 2009-08-02
I always like to get distro ISO's using bittorrent.  Sometimes it's slow, with not too many seeders; for example, I just grabbed the Kubuntu Karmic alpha off the main site, but the torrent has no seeders.  If I want to help seed, how do I combine the ISO I successfully downloaded with the stalled existing torrent?

---

### Post by rainwalker on 2009-08-02
If you downloaded a torrent of the ISO (or anything, for that matter), most torrent clients seed as you download. After it has finished, just leave the program open and it should seed the complete file(s).

---

### Post by skullmunky on 2009-08-03
Yeah, I mean what if the torrent never finishes downloading because nobody else is seeding, but I have the ISO downloaded directly from the main Ubuntu site or mirror - can I tell KTorrent to seed with that?

---

### Post by rainwalker on 2009-08-03
Hmm...I actually have no clue how to do that :?

---

### Post by huggies15 on 2009-08-03
> **rainwalker said:**
> Hmm...I actually have no clue how to do that :?

try moving the iso to the torrents dowload folder ie. if the torrent was downloading to /home/torrent/kubuntu , then move or copy your full iso to that folder. as long as its named the same as the file the torrent is downloading and is the same size then the torrent client should think it is what u downloaded via torrent and will start uploading. Ive never had the problem in linux before but that method worked once for me in XP.
Hope that makes sense?!

Steve

---

### Post by skullmunky on 2009-08-03
Cool, that worked.  At first KTorrent still thought it only had 10% downloaded.  To make it aware of the changed file, right click the torrent in the list and select "Check Data."

thanks!

---

