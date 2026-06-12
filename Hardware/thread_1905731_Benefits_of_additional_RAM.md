---
title: "Benefits of additional RAM"
date: 2012-01-07
forum: Hardware
---

### Post by wvcaudill2 on 2012-01-07
Hey everyone, I am running Ubuntu 11.10 64-bit edition on a custom Dell Studio 1558 laptop. My laptop currently has a Intel® Core™ i3 CPU M 350 @ 2.27GHz × 4 processor and 6 GB of RAM. I was wondering if my system would benefit from adding 2 extra GBs of RAM to bring the total up to 8 GBs? My local store is having some great sales on RAM, and I thought I might pick some up if it would be beneficial.

I really only use Ubuntu for web browsing, basic graphics/photo editing, and word processing, as well as the occasional movie or streaming shows or music.

What do you guys think?

---

### Post by Basher101 on 2012-01-07
take a look in your system monitor, if you stay below 80% even on max RAM load, you wont need any more..

---

### Post by aeronutt on 2012-01-07
+1, watch system monitor. Doubtful you need it, I have 3G, and rarely use 1G.

---

### Post by wvcaudill2 on 2012-01-07
I've been watching the system monitor for the past few minutes, and with only running Chromium, Dropbox, chat, broadcast, and banshee, I am using a little over 1 GB. Knowing this, I probably dont see a reason to add any more RAM.

---

### Post by MoreOrLess on 2012-01-07
If you have 3 x 2GB sticks, then adding a 4th stick will allow dual-channel operation, which will probably give a speed boost. Post result of following command to see your RAM configuration.
```
sudo dmidecode -t memory
```

---

