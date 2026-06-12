---
title: "What settings for Deluge make faster downloads?"
date: 2008-08-15
forum: General Help
---

### Post by morbid_bean on 2008-08-15
I would like to configure my deluge torrent client to speed up downloads and im not understanding what all of the settings are and do.

-Maximum Connections
-Maximum upload slots
-Maximum Half-Open Connections

---

### Post by mikewhatever on 2008-08-15
None of that matters much. The faster others upload to you, the faster download rate you get. In other words, what matters is the upload capability of clients you connect to. I suggest leaving the default settings for Deluge.

---

### Post by mb_webguy on 2008-08-15
If you're using the version of Deluge from the Hardy repositories, use the configuration wizard to get the recommended settings for your connection speed.  If you're using the version from the Deluge website, you'll probably want to change a few settings since by default everything is set to unlimited, which makes it a real bandwidth hog, and brings web browsing to a halt.  You want to at least set your overall max download speed to about 90% of your connection speed

However, as mikewhatever said, none of the settings will really increase your download speed.  If you already have port forwarding set up on your router, the only thing that will make downloads faster is selecting torrents with lots of seeders, and hopefully therefore more seeders with faster upload connections.

---

### Post by netbook_helper on 2011-07-06
I am just going to sum it up,

Find the better torrents, w/ more seeders, try using more popular sites such as, thepiratebay.org

You can always try a new bittorent client such as... Transmission, or Vuze (Azures). You can get both in the 'Ubuntu Software Center'

---

### Post by marin123 on 2011-07-06
if you use port forwarding on router, you will get normal web browsing with small bandwidth percentage, ie. i have 8 Mbit/s (500 kB/s) adsl speed and i limited torrents (transmission) to 450 kB/s, and still watch youtube videos etc with 50 kB/s...

as for torrent speeds, piratebay has sorting with most seeders, and thats how i choose torrents, with most seeders.

---

