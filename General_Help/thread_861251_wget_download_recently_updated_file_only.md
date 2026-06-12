---
title: "wget: download recently updated file only"
date: 2008-07-16
forum: General Help
---

### Post by enchance on 2008-07-16
I usually run wget -m to copy a specific folder on my server to my computer. Since wget -m "mirrors" the files by looking at each remote file then checks my local folder if I already have that file, the more files there are the longer I have to wait for it to finish checking.

Is there a way to tell wget to download just the newly uploaded files then stop once it reaches a file which I already have? I'll be able to save so much time that way.

---

### Post by bodhi.zazen on 2008-07-16
What about rsync ?

[URL="http://ubuntuforums.org/showthread.php?t=639979"]http://www.fredshack.com/docs/rsync.html
[/URL]

    [http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

---

