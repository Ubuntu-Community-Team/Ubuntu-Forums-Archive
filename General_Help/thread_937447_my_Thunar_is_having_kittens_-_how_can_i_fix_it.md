---
title: "my Thunar is having kittens - how can i fix it?"
date: 2008-10-03
forum: General Help
---

### Post by bluepowder7 on 2008-10-03
i'm not sure when exactly it happened, but Thunar (xubuntu 8.04) is having kittens, freezing, and kind of crashing.  for example, i'll open 2-3 windows to move files from one drive to another, and after a bit of useage it stops everythig - no more interaction, windows go static, if i go to another desktop and then come back they turn white (lose all visual icons), clicking on the X doesn't do anything, and in system monitor i can't end or kill it.  it's just there.  and, i can't open new instances of it.  this happens with alarming regularity as of late, and i honestly don't know when it first started doing that - i don't know if it was already being weird before my recent torrent downloads and it just got much much worse, or if it was fine before and started going nuts after those torrent downloads.

i seem to be able to use other apps just fine - but anything to do with thunar and finding or using files is just not going anywhere.  so, i can surf the web!  *sigh*

can i go into terminal and reinstall thunar somehow?  can i find out exactly what's causing thunar to freeze?

one more thing - i nearly always have my server's drives mounted on the desktop, so i'm not sure if this weirdness happens ONLY when the two are connected, or all the time.  but, since all my files are on the server, i nearly never use the desktop WITHOUT connecting to the file server.

---

### Post by bluepowder7 on 2008-10-04
bump.  anyone?

here's more info that might help:

desktop pc has XFS, and file server has JFS (with LVM running to combine my drives into one large one).  the 1.1TB of storage on the file server is nearly full, has maybe 43G of free space left.  quite a lot of files (but organized in folders, so i'd say no more than 500 in any given folder), but the slowdown has hit recently - so it's not like i doubled the number of files in total and caused it to slow.  i guess it might have a few more files than when it was working nicely, but not a LOT more.  but, maybe it's the amount of space left.  i've had the file server rebooted a few times since when i'm out of town for X days i shut it down.

the server is headless, so i can't see what it's doing while it boots up - only when it's up and running can i SSH connect to it or mount its LVM drive onto my desktop pc.

---

### Post by Jose Catre-Vandis on 2008-10-04
Are you using "tree view" or "shortcut view" ? I found tree view crashed thunar in xubuntu with compiz enabled.

---

### Post by bluepowder7 on 2008-10-04
well, i don't have compiz enabled, just the standard multi-desktop switcher thingy. i'm trying to keep it as lean as possible.  i'm using shortcut view for the left pane, and i turned off the icon preview feature.  about 10 mins ago i right-clicked on my media (movies, music, images) folder and did a "Properties", and it's gotten as far as 512 items & 135megs.  i mean, F'n SLOW!!!

---

