---
title: "mv case sensitivity"
date: 2008-09-22
forum: General Help
---

### Post by alancanniff on 2008-09-22
Hello,
I'm running Ubuntu 8.04

I've a directory called 'text' which I want to move to 'Text' but I'm getting this error

```
$ mv text Text
mv: cannot move `text' to a subdirectory of itself, `Text/text'
```

as far as I can tell, it's not differentiating between 'Text' and 'text'...
I even tried and I can cd into the directory using either 'text' or 'Text'

It's not a serious problem but I know that linux is case sensitive so I'm confused as to why this is happening.

Any explanation would be welcome.

---

### Post by Denestria on 2008-09-22
Is it on a samba share?  Or on a non-linux type of filesystem like vfat?

---

### Post by alancanniff on 2008-09-22
> **Denestria said:**
> Is it on a samba share?  Or on a non-linux type of filesystem like vfat?

Yes, it's on a FAT32 files system.

---

### Post by phidia on 2008-09-22
Don't you need to specify the path? For example "mv text /mnt/windows/home/user/Text"
I don't know what your specific path is obviously but I think that's what this is saying: > mv: cannot move `text' to a subdirectory of itself, `Text/text'

---

### Post by Yannick Le Saint kyncani on 2008-09-22
> **alancanniff said:**
> Yes, it's on a FAT32 files system.

Yeah, well, that explains it. Fat32 is case-insensitive, so text and Text are the same thing in a fat32 filesystem.

---

### Post by alancanniff on 2008-09-22
Thanks you kindly for your help, That's been annoying me all day.

---

