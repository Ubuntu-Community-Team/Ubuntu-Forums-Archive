---
title: "need help with script file"
date: 2008-09-23
forum: General Help
---

### Post by Steel Reign on 2008-09-23
hey guys,
    i am kinda of still new to ubuntu. so excuse the question. i need to know how to create a script file that will copy from one directory to another. so far i have:

#!/bin/sh
cp /root/WFM/content/FL State News - No Weather /media
/Storage_Drive/news
cp /root/WFM/content/FL State News - No Weather /media/Storage_Drive/weather

i have tried this and ran it in terminal, but keep getting errors that those directories don't exist and indeed they do.

any help would be great.

thanks.

steel reign

---

### Post by fragos on 2008-09-23
I would think "- No Weather " is your problem. cp src dest. Also command line doesn't do well file names with spaces in them.

---

### Post by Pom2122 on 2008-09-23
cp (and a lot of linux commands) doesn't like spaces. 

```
cp "/root/WFM/content/FL State News - No Weather" /media/Storage_Drive/news
cp "/root/WFM/content/FL State News - No Weather" /media/Storage_Drive/weather
```

---

### Post by Steel Reign on 2009-06-11
Thanks I will try taking out the spaces.

---

