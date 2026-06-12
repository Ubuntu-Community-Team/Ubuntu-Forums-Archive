---
title: "Trash file directory loop error"
date: 2008-11-22
forum: General Help
---

### Post by jlook on 2008-11-22
I wanted to backup my newly loaded music files, so I tried out a backup program ... which worked fine EXCEPT that I wasn't thinking clearly and I set up the backup folder within my user folder under $home ... and of course I wanted to backup everything in my user folder, so I set that to backup.

Well it looped endlessly backing up its own backup, and now I have a "backup" folder within my user folder that I can't seem to delete ... and of course it's kinda LARGE!

Can anyone tell me how to get around ... I guess it's the file protections ... to delete that folder?  Like in windows (I know, I hate windows too, but I can't stop thinking in that mode!!), I could do file maintenance in DOS or in a command prompt. Anything like that with Ubuntu?

Thanks!
jlook

---

### Post by john183 on 2008-11-22
If you stop the backup program first you should be able to delete the backup folder via the terminal (Applications>Accessories>Terminal) and run the following code where "folder" the the name of your backup directory sans quotes
```
sudo rm -r "folder"
```

Make sure you are in your home directory, i.e. make sure the terminal prompt ends with "~$" When i am in my home home directory the prompt reads:

```
jr@ubuntu-laptop:~$
```

---

