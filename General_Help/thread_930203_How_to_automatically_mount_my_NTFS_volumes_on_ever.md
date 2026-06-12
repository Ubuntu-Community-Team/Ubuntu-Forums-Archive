---
title: "How to automatically mount my NTFS volumes on every boot?"
date: 2008-09-25
forum: General Help
---

### Post by divisortheory on 2008-09-25
I have a dual boot with Windows XP and sometimes I want to access my NTFS partition in Ubuntu.  What I've noticed is that if I go to the "Places" menu in Gnome, my NTFS volume is listed there.  Once I click on that, it drops an icon onto my desktop that allows me to access it later from the desktop.  But there seems to be more to this than meets the eye.

I loaded up a media player and pointed it to my music collection on my NTFS partition.  It dutifully loaded all the files and played them no problem, and saved my collection.  I rebooted and immediately launched the media player again and it said my collection could not be found.  Exiting the media player and clicking the icon for my volume in the Places menu, then going back into the media player, all of a sudden my media player could now see all the files.  So what exactly is happening when I click that menu item, and how do I make it happen every single boot automatically?

Thanks

---

### Post by drs305 on 2008-09-25
One of the easiest ways of dealing with ntfs partitions is to install "ntfsprogs" and  "ntfs-config". ntfs-config will set up your ntfs partitions for mounting and read/write:
```
sudo apt-get install ntfsprogs ntfs-config
sudo ntfs-config
```

---

