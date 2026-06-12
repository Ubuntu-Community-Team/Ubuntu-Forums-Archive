---
title: "renaming mounted ntfs drives"
date: 2008-05-03
forum: Hardware
---

### Post by tMV on 2008-05-03
Hello
I used ntfs configuration tool to mount NTFS drives with certain names (media\xxx) and now I want to change those names, how can i do this?

---

### Post by halfhaggis on 2008-05-03
The mount points are defined in fstab, located at /etc/fstab

You could directly edit that file to change the mount points, but if you are using gnome it might be possible to do it via the gui.

Places>Computer

Right click on the volume you want to change, and select properties.
Under the  "Volume" tab, click settings.
One of the options is "Mount Point"

I haven't tried it though.

I know that editing fstab *will* work, but you need to exercise caution because if you make an error somewhere, you might not be able to mount root.

---

