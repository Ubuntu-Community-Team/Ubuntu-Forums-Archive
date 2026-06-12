---
title: "HOWTO: Subscribe to RSS feeds in Thunderbird from Firefox"
date: 2008-11-09
forum: General Help
---

### Post by gexcko on 2008-11-09
After much hair-pulling I've managed to get firefox 3 and thunderbird to play nice in intrepid when it comes to 'clicky' rss feed subscriptions. Some of the other solutions didn't work as thunderbird couldn't validate any feed that didn't start with http:// (ie: feed://) .. so here's a quick fix...

sudo nano /usr/local/bin/thunderbird-add-feed.sh
```
#!/bin/sh
# ensure all feeds passed to thunderbird begin with http
feedurl=$1
feedurl=${feedurl##feed}
/usr/bin/thunderbird -mail feed:`echo http${feedurl##http}`
```

Run **sudo chmod +x /usr/local/bin/thunderbird-add-feed.sh** to finish it off then in firefox simply use that script to handle rss feeds instead of pointing it directly to thunderbird.

---

