---
title: "[SOLVED] Moved my home folder to separate partition"
date: 2008-09-12
forum: General Help
---

### Post by YldGuy on 2008-09-12
I moved my home folder to a separate partition yesterday according to this [guide]("http://www.google.co.in/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.psychocats.net%2Fubuntu%2Fseparatehome&ei=JhrKSNH4MKa6swLP4tmdCg&usg=AFQjCNEgtQIp0sc6F_WAqYNPUU0gWq8PXg&sig2=_t3TsOgp6PqTLp9QNJ21Gw"). All went well and I got the home folder on the separate partition. However, when i started firefox after that, my bookmarks toolbar was gone. and the google search box wont work. it can open up pages though. Then i removed firefox, deleted the .mozilla folder and reinstalled firefox, added bookmarks toolbar and all was well. i still need to try importing the bookmarks and see if it works but my hunch is it will. And oh, another thing, in my new home some of the folders were marked as readonly, including .mozilla, read and write being authorized to root only. i finally went to terminal, typed sudo nautilus and changed the permissions manually for each folder. In some cases, it went deep into folders within folders. I don't know if the bookmarks toolbar were absent coz of permissions as it didn't occur to me at that time. 

my question is, why would some folders permission change like this? my home is now working fine and all the apps also work fine. just wondering how can the permissions change?

---

### Post by Sef on 2008-09-12
Moved to General Help.

---

### Post by YldGuy on 2008-09-27
i dont know what happened back then but most of the subfolders within home were defaulted to root as owner.. just fixed it all by chown -R.

---

