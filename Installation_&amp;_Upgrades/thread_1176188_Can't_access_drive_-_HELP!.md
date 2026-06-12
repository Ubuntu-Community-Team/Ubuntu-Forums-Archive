---
title: "Can't access drive - HELP!"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Ausmo on 2009-06-02
Hi,

I am a new user. Following installation of Ubuntu, I am unable to see/access the local C: drive in Ubuntu :(. Unfortunately this is the location of most of my existing files. External drive and CD drive are visible and accessible with windows (Vista). 

Help with this would be appreciated.

Regards

Erik

---

### Post by theDaveTheRave on 2009-06-02
Ausmo

how did you install ubuntu? from a live CD??

If so, try with the live CD again and see if you can navigate to the C:

I am guessing you are staying with a dual boot? I guess also that you haven't "partitioned" your drive?

Most often the drives come up in the < /media/ > subdirectory of your ubuntu box (or at least they do for me!), if they are USB or CD/DVD drives, otherwise /dev/disk/ is the place to look to see how many there are there.

Also in your "file manager" (nautilus if you are using Gnome ~ something else for KDE and X), you should have a "side pane", it can be turned on / off in the <view> menu.

if you turn it on and then select "places" from the list that appears at the top of the pane, it should show up the external / unmounted drives.

does this help you in your solution??

if not and you are still unable to "see" your HDD try this from a command line
```

ls /dev/disk/by-id

```

this simply lists all the HDD devices connected to the system that you have available.
after this check the mounted partitions
```

mount

```

and see if all the info between them tallies up... or if you aren't certain post the output here.

David

---

### Post by Ausmo on 2009-06-02
> If so, try with the live CD again and see if you can navigate to the C:


Thanks that worked. Help much appreciated.

Erik

---

### Post by theDaveTheRave on 2009-06-02
Ausmo

Glad to be of assistance.

just quickly though....

I assume you had just done a fresh install and had no "important" data anywhere, then just re-installed ubuntu from the CD.

Is that correct?

or was there some other step you took?

If it was just an issue with your first installation procedure, do you have any idea where you went wrong the first time around?

If you have just stuck in the live CD and booted to that, what happened when you re-booted to the main system? Or did you do something else whilst using the live CD that made the HDD visible.

I'm curious exactly what was wrong, and what the full solution was.

either way I'm glad everything is working for you.

David

---

