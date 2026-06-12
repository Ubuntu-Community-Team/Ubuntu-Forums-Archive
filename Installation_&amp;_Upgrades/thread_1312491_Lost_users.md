---
title: "Lost users"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by dclement on 2009-11-03
Hello,

I have a user issue after installing Karmic.

I thought I had done things cleanly, with a separate /home. I reinstalled (rather than upgraded), then I proceeded to recreate the users (whose /homes had been preserved in their own partition).

2 of them (out of 4) show the following problem upon connection:

"could not update /home/(username)/.ICEauthority" then

"There was a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 died with status 256)"

After this, I get an empty desktop without any menu bar.

I thought best to first ask for advice here before trying anything I could regret...

TIA - best regards, Daniel

---

### Post by OriginalName on 2009-11-03
Looks like permissions problems... I'd copy the data out of the /home folders (copy to something like username.backup) and then wipe them... when the user logs in gnome (or kde) should recreate anything it needs... then you can copy the data back in.

---

### Post by dclement on 2009-11-03
I was thinking of that kind of solution myself. I'm pretty sure it will work, this way.

Puzzling, however, that only 2 of 4 users had been affected by this problem. I'll keep this in mind for my future "upgrades"...

Thanks - Daniel

---

### Post by Bruce H on 2009-11-03
You could try this also. From a terminal:

```
sudo chown -R user:user /home/user
```Substitute "user" for the appropriate user names, obviously.

---

### Post by dclement on 2009-11-05
Yes, that will probably be my simplest option.

I keep wondering, though, why *some* users had this problem, since I re-created them exactly as they were before the new install...

---

