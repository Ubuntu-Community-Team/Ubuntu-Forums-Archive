---
title: "Crazy crons"
date: 2008-11-04
forum: General Help
---

### Post by easoukenka on 2008-11-04
For some reason some of my crons are running about every minute?  I am very confused as this is  a new problem was working fine.  Here is my crontab.

30 4 * * * /home/eric/compiled/scripts/movie_indexer >/dev/null 
0 0 * * 1 rm temp/* >/dev/null
* * * * * getmail >/dev/null 
* 23 * * * rm /home/eric/.mc/history /home/eric/.bash_history > /dev/null
* 2 * * * /home/eric/compiled/scripts/vbgrace > /dev/null
* 21 * * * screen -dmS programs rtorrent 
* 6 * * * screen -dmS programs rtorrent 
* 7 * * * touch test


For sure the last 3 run every minute  I even moved the  touch command to the top and they ran every minute also.  I don't believe the other ones are running off schedule though.

Thank you for any tips

---

