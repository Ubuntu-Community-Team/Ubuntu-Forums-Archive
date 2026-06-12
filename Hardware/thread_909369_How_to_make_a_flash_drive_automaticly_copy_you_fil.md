---
title: "How to make a flash drive automaticly copy you files."
date: 2008-09-03
forum: Hardware
---

### Post by modmadmike on 2008-09-03
So while I was at school I made a cool yet simple new script on my flash drive that copies the Documents folder when inserted. Here is the script:

```
#!/bin/sh
cp -r "/home/INSERT_USERNAME_HERE/Documents" "/media/disk/"
```

Then save the file as autorun.sh in the devices root directory.

---

