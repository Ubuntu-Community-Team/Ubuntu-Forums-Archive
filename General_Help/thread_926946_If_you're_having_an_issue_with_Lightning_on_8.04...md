---
title: "If you're having an issue with Lightning on 8.04...."
date: 2008-09-22
forum: General Help
---

### Post by jakev383 on 2008-09-22
Hopefully this will help someone else out;
I did a fresh install of 8.04 on my laptop. Installed Thunderbird from the repos, and then downloaded the Lightning plugin so I can have a calendar.
All looked like it went well, but the calendar would not work. I could not add any appointments, events, etc.
After a bit of searching, it seems the plugin requires libstdc++5, but 8.04 only installs libstdc++6.  The fix was easy, once found:
```
apt-get install libstdc++5
```

---

### Post by kokkus on 2008-09-22
Should be moved to Tutorials & Tips.

---

### Post by cjax1 on 2008-11-02
Thanks jakev383. I was having the same problem the last two days when Lightning updated to version .9 and you helped me solve it. I see some other threads about the same problem. It seems there's more than one way to solve this but installing libstdc++5 did it. But, after installing libstdc++5 it seemed to wipe out my TB profile. I had three accounts in TB, two of them were gmail IMAP accounts. They all were gone. TB prompted me to create a new account. But I had a backup of my profile which had Lightning .8 and when I restored the backup Lightning was back up and running even after re-updating Lightning to .9 again. Before installing libstdc++5 even my backed up profile didn't help. Anyway, I finally got it fixed. Thanks

---

