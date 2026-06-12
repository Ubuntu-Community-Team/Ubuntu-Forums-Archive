---
title: "[SOLVED] Root owns a file I want to get rid of"
date: 2008-08-02
forum: General Help
---

### Post by captainhydrollama on 2008-08-02
OK I need help there are some remnant playonlinux files on my computer that root owns so I cannot delete them how would I go about remedying that problem?

---

### Post by cdtech on 2008-08-02
First you should try "sudo apt-get autoremove && sudo apt-get clean"

I would think.....

---

### Post by tamoneya on 2008-08-02
alt-F2 ```
gksudo nautilus
```

---

### Post by captainhydrollama on 2008-08-02
> **tamoneya said:**
> alt-F2 ```
gksudo nautilus
```

thank you so much!!! I apologize for my noobishness but this did the trick thank you!

---

### Post by tamoneya on 2008-08-02
no problem.  Make sure to be very careful when using it though and make sure to close it when you are done because it can do some VERY serious damage.  Also mark this thread solved if you could.  It is to the top right of the first post under thread tools.

---

