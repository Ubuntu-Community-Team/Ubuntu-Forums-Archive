---
title: "Adding Another HD to Ubuntu box"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by Feenix217 on 2007-11-03
Hey there!

I'm running Gutsy Gibbon and it's fully updated.

I've also added a second HD to my GG box, have formatted it, etc. and can mount it but when I try to edit /etc/fstab via gedit so the system will allow me to add/change the contents of the HD, it says that I don't have permission to edit fstab.

So what to do?

Feenix217

---

### Post by ofb on 2007-11-03
You'd have to be root to edit a system file like fstab.

So, in a terminal you would enter

```
gksudo gedit /etc/fstab
```

But before you edit fstab, you really should make a backup copy, so do

```
sudo cp /etc/fstab /etc/fstabBAK
```

---

### Post by bonestonne on 2007-11-04
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
^another method would be forcing yourself to have ownership/permission to edit the files. a while ago i remember needing to use that method to get ndiswrapper working...i had to force permissions on a few files to use them.

then you could

```
sudo gedit [path/filename]
```

all you want to that file. a very simple solution, but takes more work than the previous suggestion

---

### Post by Feenix217 on 2007-11-04
Hey there!

I did what the first replier mentioned and then was able to edit /etc/fstab.

Now when the GG box reboots, the drive is mounted and I can add/delete files to it!

Thanks for the help!

Feenix

---

### Post by ofb on 2007-11-04
Glad it's fixed. Here's how to mark your thread as Solved,
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

