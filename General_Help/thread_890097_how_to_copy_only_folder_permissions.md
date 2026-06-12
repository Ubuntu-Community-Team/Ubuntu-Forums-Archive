---
title: "how to copy only folder permissions"
date: 2008-08-14
forum: General Help
---

### Post by uMuppet on 2008-08-14
I recently copied my /var folder to a new drive as it was getting too big for the small partition.  I copied it using thunar file manager.  Every folder permission under /var is now root:root with 755 access.  
I have another PC with the correct permissions, can I somehow copy just the folder properties for all folders under /var and paste them into the broken PC?

---

### Post by bodhi.zazen on 2008-08-14
cp -dpr

This is one reason people use tar ;)

[http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving](http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving)

---

