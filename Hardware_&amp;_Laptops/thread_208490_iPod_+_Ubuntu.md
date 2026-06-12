---
title: "iPod + Ubuntu"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by mllr on 2006-07-03
How can I use my iPod in the Ubuntu?

---

### Post by Mike_N on 2006-07-03
Yuppers, I think that Banshee will interface with it as well as GTK Pod... Prolly a dozen ways to do it actually.

---

### Post by doris.houng on 2006-07-03
I'm using [Quod Libet](http://www.sacredchao.net/quodlibet) (my music player of choice) with the [iPod plugin](http://www.sacredchao.net/quodlibet/wiki/Plugins/iPod).  :)

---

### Post by mllr on 2006-07-03
i installed banshee and its running xD

thx

---

### Post by lptr on 2006-07-04
First a small documentation for those who want to feed their iPod with Dapper. Then later my own question regarding iPod.

Dapper usually automounts device on desktop. All filenames of stored songs are located on iPod device under /iPod_Control/Music and are renamed literally - hm - orphaned. I would say really strangely organized by iTuned software.

I for myself followed the mentioned Projects here in thread:
```
http://banshee-project.org/Distributions/Ubuntu
```

Installed this one as described on page (sources.list needs indeed the reference to breezy not dapper, though). I searched for infos how to use iPod with banshee to connect device - maybe downloading/syncing songs, videos, pictures and the like. Could not find anything.

Some tries with Banshee and I found out, that only with the appearing start window and the button in the right lower edge it is possible to select an import source. There you need to select /media/sdb2 or wherever device is to be found. Banshee will read in infos and display songs. But nothing else.

I found that GTKPOD seems to be quite sufficient, too. No change in sources.list or the like is necessary. Start Adept and search for and install it.

All that is needed with it is a sym link to mounted harddisk device of iPod. Mine is currently at /dev/sdb2 that will be automounted to /media/sdb2. Because GTKPOD seems to have a hard coded /media/ipod, I sym linked to it with this:
```
sudo ln -s -T /media/sdb2 /media/ipod
```

Now my own question:
I am playing myself with both solutions. What I am really missing is the sync of pictures and especially videos. Is this possible anyhow?

Any insights?

rob*/

---

### Post by Blind-Summit on 2006-07-05
And how do I get m4v videos onto the iPod

Nothing seems to be able to manage to do that

---

### Post by Blind-Summit on 2006-08-08
Can I use iTunes via WINE to do this I've still not found any other method that will work.

---

### Post by lptr on 2006-08-08
Hello Blind-Summit,

some time ago I tried a beta of XOverOffice from Codeweavers. This installs a pretty old iTunes SW :sad: .

iTunes itself worked. But iTunes told me, that my iPod device cannot be found. I expect that a specific sym link needs to be set as it was necessary with GTKPOD (I described this previously).

Maybe anybody out there who solved this?

rob*

---

