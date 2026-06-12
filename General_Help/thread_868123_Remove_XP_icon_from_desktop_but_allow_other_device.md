---
title: "Remove XP icon from desktop but allow other devices?"
date: 2008-07-23
forum: General Help
---

### Post by stormtrooprdave on 2008-07-23
I have XP and Ubuntu on dual boot.  I want to remove the XP icon from the desktop but still be able to have icons for USB sticks, mp3 players, etc.

If I use Configuration Editor - apps/nautilus/desktop - and untick volumes_visible it makes the XP icon disappear but then when I plug in a device it doesnt show up on the desktop.  This is what I want to avoid.

I also cannot edit fstab to noauto mount as all my media is on the XP partition.  Yes I could just mount the XP partition when I need it but my desktop backgrounds and skydome are also on the XP part so I have blank backgrounds at startup which is unacceptable.  

Yes I could save the backgrounds to the Ubuntu partition but I don't see why I should have to duplicate files.  I don't want a workaround, I want to know how to get it to do exactly what I want.

---

### Post by Elfy on 2008-07-23
There is a post by aysiu which suggests mounting a drive away from /media would cause it to not be visible on the desktop

[http://ubuntuforums.org/showpost.php?p=1386537&postcount=2](http://ubuntuforums.org/showpost.php?p=1386537&postcount=2)

Would mean creating a directory for it to mount in and editing of fstab. Easy to accomplish - but I don't actually know if it works as the thread comes to a halt.

If you need help with that, run these commands and post results here

```
cat /etc/fstab
sudo fdisk -l
```

---

