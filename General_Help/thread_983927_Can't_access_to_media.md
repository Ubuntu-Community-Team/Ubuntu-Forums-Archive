---
title: "Can't access to media"
date: 2008-11-16
forum: General Help
---

### Post by Fullmetalz on 2008-11-16
Hi everyone im new to ubuntu and so to the forum. This is actually my first post. So I have a problem... Yesterday i could access to the media device wich is my windows partition with no problems... Today I double click on it and nothing happens.So I cant access to media nor to dvd reader,the only device I can access from ubuntu it's to the file system (ubuntu partition). Can someone help me with this? I hope so...

---

### Post by mgol on 2008-11-16
Please post results of commands:
```
cat /etc/fstab
ls -l /dev/disk/by-uuid
mount
```

---

