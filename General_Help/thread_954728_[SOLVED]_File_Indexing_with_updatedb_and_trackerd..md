---
title: "[SOLVED] File Indexing with updatedb and trackerd. Are they overlapping and/or needed"
date: 2008-10-21
forum: General Help
---

### Post by bksunday on 2008-10-21
Hi,

While waiting for trackerd to index files so I can search for something I can't remember, I used the locate tool (which worked fine!) and I was trying to figure out if it uses the same database trackerd was actually indexing.

I figured that updatedb seems to update with a cron job.

I heard all the rants about trackerd being resource hungry but I really like the search front-end.

But no, I don't want 2 applications indexing my same files (on top of picasa on startup, amarok and all others)

So, the following questions arise:

Do both tools use the same database? (in my dreams probably)

Does the locate tool and updatedb are used by system applications meaning I shouldn't disable it or can I?


Thank you!

---

### Post by niteshifter on 2008-10-21
Hi,

locate and tracker use different database files and schemes.
locate's db file is at /var/lib/slocate/slocate.db
tracker's is at /home/<user>/.cache/tracker/ and contains several different indexes.

Note the difference: one (locate) is a system wide database of file locations. The other (tracker) is unique to a user. Also, these two indexers do very different things: locate quickly finds text in file system paths only. It doesn't index file _content_. tracker does that. tracker, unless you specify to crawl / won't be looking in /usr, /var etc. (which then ups it's resource use, particularly checking for updates).

I don't know if system utils do use slocate - don't know that they don't. Each of the two tools has it's use, so I leave them be. Plus, locate is very handy to have around when the GUI isn't around.

---

### Post by bksunday on 2008-10-21
Thanks a million niteshifter =)

---

