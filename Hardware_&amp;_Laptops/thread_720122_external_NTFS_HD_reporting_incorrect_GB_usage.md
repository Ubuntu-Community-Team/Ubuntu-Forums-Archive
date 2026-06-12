---
title: "external NTFS HD reporting incorrect GB usage"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Dustout on 2008-03-09
[IMG]http://img183.imageshack.us/img183/8986/harddriveul3.png[/IMG]

Last night i was copying some 1080p videos from one NTFS external to my other NTFS external. The next day i check for those videos and the folder is empty but the HD is saying that 70GB is in use.


Now i am sure formatting the HD will fix this problem, but is their a way to recover these files since these videos took along time to get?

---

### Post by Jimmey on 2008-03-10
Press CTRL + H to see hidden files. 

Check for a .Trash folder.

If that fails, try using photorec ```
sudo apt-get install testdisk
```.

Let me know how it goes!

---

### Post by Dustout on 2008-03-10
unfortunately the .trash folder isn't the issue (wish it was tho, cause it would of made things allot easier)

i'm running a scan on my harddrive right now *praying it finds the files*

---

### Post by Dustout on 2008-03-10
i ran testdisk and it didn't find anything, so i guess i'll just have to bite the bullet on this one :(

*formats HD to ext3*

---

### Post by Jimmey on 2008-03-10
No, don't do that.

run photorec from the terminal!
```
sudo photorec
```

---

### Post by Dustout on 2008-03-10
shoot :mad:

ohh well i guess it isn't that big of a loss since my computer cant even run 1080p mkv videos. So from now on when i get HD stuff it'll be in 720p 

thanks for your help Jimmey

---

### Post by Jimmey on 2008-03-11
Aslong as you've not written anything more to the drive, those files might still be recoverable. Try anyway!

---

