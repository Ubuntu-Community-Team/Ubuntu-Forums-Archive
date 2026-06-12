---
title: "How to automatically extract downloaded files?"
date: 2008-10-16
forum: General Help
---

### Post by ledibri on 2008-10-16
Popular situation: you download archive files (zip, rar, ...), and almost everytime you need to extract them. Again and again you go to download folder and extract downloaded files.

So, why don't make this process automatic?
1. Downloaded file extracts itself.
2. After extraction it is deleted.

Any ideas?

---

### Post by Diabolis on 2008-10-16
Most of the people achieve this from the command line. For example if you want to download this file: *[http://lastagent.googlecode.com/files/lastagent-0.2.05.tar.bz2](http://lastagent.googlecode.com/files/lastagent-0.2.05.tar.bz2)* you would run this:
```
**wget** http://lastagent.googlecode.com/files/lastagent-0.2.05.tar.bz2; **tar** --bzip2 -x -f lastagent-0.2.05.tar.bz2; **rm** lastagent-0.2.05.tar.bz2
```

Depending of the file type the arguments for the command tar will change.

---

### Post by ledibri on 2008-10-17
So, it downloads and extracts, but file is still there.

And the problem is you have to write in command line, wchich I think would take more time than extracting manually.

---

### Post by vanadium on 2008-10-17
1) the file is being removed. 2) For experienced people, the command line approach will be faster.

I would be reluctant in having a downloaded file automatically extracted without me explicitly asking it. It would nevertheless make a sensible feature for people wanting this behaviour. Did you check whether a Firefox plugin exists with this functionality?

---

### Post by ledibri on 2008-10-17
> Did you check whether a Firefox plugin exists with this functionality?

Yes, I did, but there isn't one.

---

### Post by Diabolis on 2008-10-17
You could check for a **nautilus script** also. Someone on the forums has a thread with many of them and **gnome-look** has a section for them too.

---

