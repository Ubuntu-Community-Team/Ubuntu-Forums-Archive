---
title: "Back up Preferences in Mozilla?"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Hellstudios on 2009-03-19
all I really do on my computer is surf the net and play games. so I won't really mind doing a Fresh install on my new SATA hard drive, but how do I back up everything I've ever done in Mozilla to a USB stick? thats all I want to do and I'll be happy. Since I have like 800 Bookmarks and saved Passwords I'd Hate to get rid of.


Thanks, 
Hellstudios

---

### Post by Tim Sharitt on 2009-03-19
Save your ~/.mozilla folder. It contains all you bookmarks, saved password, extentions, etc. Replace the ~/.mozilla folder on your new install with your backup copy and everything should be just like it was on on the old system.

---

### Post by Hellstudios on 2009-03-20
where do I find that folder?


sorry for the late reply / bump.

---

### Post by Tim Sharitt on 2009-03-21
The .mozilla folder is in your home folder (/home/username/). ~ is just your home folder, /home/username/folder is the same as ~/folder. 
The .mozilla folder ( or any other folder of file name beginning with . ) is hidden. To see it in nautilus, got to View > Show hidden files or ctrl+h. To see it with ls in the terminal you'll need to add the -a option.
```
ls -a
```

---

### Post by SuperSonic4 on 2009-03-21
```
cp -Rfv ~/.mozilla /media/disk
``` will copy the mozilla folder and it's contents to /media/disk (which I believe are what removeable devices are mounted as).

---

