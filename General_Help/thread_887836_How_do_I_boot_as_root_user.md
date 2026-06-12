---
title: "How do I boot as root user?"
date: 2008-08-12
forum: General Help
---

### Post by colobix on 2008-08-12
I have to boot ubuntu as admin to manage read/write settings in directories, so how do I do that?

Thanks.

---

### Post by Nepherte on 2008-08-12
Instead of logging on as administrator, which is disabled by default with reason, try using the same commands but with sudo in front of it. Here's some more information: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by snowpine on 2008-08-12
You don't need to boot as root, you just need to preface commanads with sudo or gksu to temporarily gain root privilages. For example, 'gksu nautilus --no-desktop' will allow you unrestricted access to the filesystem.

---

### Post by Ryadt on 2008-08-12
Try using nautilus as root```
gksudo nautilus
```

---

### Post by gjoellee on 2008-08-12
logging in as root, compromises Ubuntu's security!

---

### Post by colobix on 2008-08-12
Thank you so much folks. Quick replay and great expained:)

---

### Post by aysiu on 2008-08-12
As others have pointed out, you don't have to log in as root to make root-permission changes to your system.

I'm also going to mention that there are very few situations in which it is appropriate to change the permissions of root-owned files. Sometimes doing so can break your system. You can modify files in root-owned directories (I'd advise backing them up before modifying them, of course), but do not change ownership or permissions of those files unless you absolutely know what you're doing.

---

