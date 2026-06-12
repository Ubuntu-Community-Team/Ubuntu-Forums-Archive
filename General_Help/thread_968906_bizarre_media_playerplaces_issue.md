---
title: "bizarre media player/places issue"
date: 2008-11-03
forum: General Help
---

### Post by saladbar2000 on 2008-11-03
I have a new bizarre problem.  When I click on places on the desktop, it pulls up the media player.  Any suggestions?

---

### Post by deprecat on 2008-11-03
Err, never seen it before, have you checked your sysconfig?

---

### Post by saladbar2000 on 2008-11-03
how and what would I be checking?  Is there anyway I'm missing the filebrowser?

---

### Post by saladbar2000 on 2008-11-03
The file browser is working because I can pull it up when I click on Places >> Computer but the media player is pulled up when I click on Home folder, documents, videos, music, etc.  I looked at main menu, appearance, and preferred applications but didn't see anything talking about file browser settings and I didn't see anything in the file browser settings.  

When it first happened, it pulled up the kaffeine player and I thought the kaffeine player was the problem so I removed it.  Now the Mplayer comes up with the error message "seek failed."  

Any help would be greatly appreciated.

---

### Post by plucky on 2008-11-03
> Any help would be greatly appreciated.


See this [bug report](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

To fix,from a terminal ```
nautilus
```

Right click on a folder and select open with"Open with Other Application" and select **File Browser**

Good Luck

---

### Post by saladbar2000 on 2008-11-03
thanks
it looks like that did the trick.

---

