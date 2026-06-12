---
title: "Ibex - Firefox not showing history or bookmarks"
date: 2008-11-04
forum: General Help
---

### Post by lozparry on 2008-11-04
Hi, I installed 8.10 last week and all was well until last night and firefox now doesn't show any history or and bookmarks I had? 
All I have done is add VMware server 2 and this has a web admin page access? This worked on the day I installed it with installing a vista vm? at the moment it always seems to be refreshing (on the tab) and the back/forward/refresh arrows are greyed out?
I have 64bit version btw...

thanks

---

### Post by Elfy on 2008-11-04
Not sure if you can get the history back but open the bookmark organiser - then Import and Backup - Restore should have a backup of the bookmarks.

> If you lost your bookmarks within the last five days, you can restore them from the set of backups that Firefox maintains. 
[http://support.mozilla.com/en-US/kb/Lost+Bookmarks](http://support.mozilla.com/en-US/kb/Lost+Bookmarks)

---

### Post by lozparry on 2008-11-05
Thanks, but I already tried that and I get a message unable to process. I dont even have the ubuntu bookmarks or firefox ones!

---

### Post by lozparry on 2008-11-05
Well, solved! I have just re-installed 8.10, start again and hopefully dont get the same issue!

---

### Post by bhathco on 2008-11-05
I have the same issue. My bookmarks do not get retained. It's like I'm starting from scratch everytime I open Firefox. What gives?

---

### Post by lozparry on 2008-11-05
Sorry, all I know is it stopped working the day after I installed VMware2 which has a web admin page and needed add-ons to work. It worked to begin with as I loaded vista in Vmserver but the next day that didnt work either?
I also installed Java for some reason!

---

### Post by brundles on 2008-11-09
> **lozparry said:**
> Sorry, all I know is it stopped working the day after I installed VMware2 which has a web admin page and needed add-ons to work. It worked to begin with as I loaded vista in Vmserver but the next day that didnt work either?
I also installed Java for some reason!

OK, so it looks like VMWare2 kils Firefox on Ubuntu - that's exactly the same problem I've had and although I was suspicious of the VMWare install as the trigger, didn't have enough to confirm it. At the moment I've got the kernel upgrades pinned to avoid messing with the VMWare install but I'm wondering if running one of those will fix it.

If I find anything else on fixing it (we can't be the only ones!) I'll post back.

---

### Post by Elfy on 2008-11-09
First make sure that in Edit Preferences - Privacy Tab that always clear private data isn't set.

If not try it after making a new profile - start firefox from aterminal

```
firefox -P
```

---

