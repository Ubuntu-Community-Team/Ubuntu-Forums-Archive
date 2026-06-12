---
title: "[SOLVED] Tracker doesn't search for common link words"
date: 2008-08-24
forum: General Help
---

### Post by jackn on 2008-08-24
I'm pretty pleased with Tracker, personally, although I do see a lot of griping around the forums.

I've just noticed, however, that it doesn't index basic common words such as 'and', 'even', 'still', etc.

I would like it to index all words.

Can this be modified? Does it have to do with the ceiling to be set on unique words to be indexed in 'Preferences'? I doubt it, but I'm at a loss.

Thank you,
jackn

---

### Post by jackn on 2008-08-24
Jamie, the main author (I believe) of Tracker, was kind enough to let me know that there's indeed a list of "stop words" which Tracker won't index.

It is to be found in ```
/usr/share/tracker/languages/stopwords.en
```

I backed it up:
```
mv path path.backup
```
and then emptied the original file (gedit file, select all, suppress).

Of course, this requires reindexing. 
I'm not sure whether I need to do anything for reindexing to occur. 

Will keep you posted.

---

### Post by jackn on 2008-08-25
It worked.

It is necessary to tell Tracker to re-index.
This can be by righthand clicking on the Trakcer icon (top rightand corner of the screen) and clicking on re-index in the dropdown menu.

Thanks to Jamie and to the other developers of Tracker.

jackn

---

