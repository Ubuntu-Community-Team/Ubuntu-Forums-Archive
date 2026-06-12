---
title: "contents of all text files in the windows partition(mounted) turn into messy code"
date: 2008-09-07
forum: General Help
---

### Post by kevintse on 2008-09-07
HI, there,
I have successfully mounted the Windows NTFS partitions in my new Ubuntu system, which has a locale of en_HK.UTF-8, but the contents of all text files turn into messy code, i can't get them display Chinese. the filenames are displayed correctly in Chinese though.

I have tried all these, but in vain
```
sudo mount /dev/sda5 /media/c/ -t ntfs-3g -o defaults,locale=en_HK.UTF-8,nls=utf8,iocharset=utf8,umask=0222 

sudo mount /dev/sda5 /media/c/ -t ntfs-3g -o defaults,locale=en_HK.UTF-8,nls=gbk,iocharset=gbk,umask=0222 

sudo mount /dev/sda5 /media/c/ -t ntfs-3g -o defaults,locale=en_HK.UTF-8,nls=gb2312,iocharset=gb2312,umask=0222 

```

---

### Post by kevintse on 2008-09-07
no, it has sunk...anybody knows how to do that?
please give me a clue...

---

