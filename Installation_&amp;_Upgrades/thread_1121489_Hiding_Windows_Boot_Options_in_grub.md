---
title: "Hiding Windows Boot Options in grub"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by stepram on 2009-04-10
Just Like to say Thanks to everyone on here for their help in configuring grub and share and trick i picked discovered.   If like we, you still want a Microsoft Vista or XP windows partition but don’t want to be reminded of it all the time you can hide the windows options but still keep them available should you need them.

When you leave the title and root line’s in the divider section, but remove the dividing text, grub not only places a blank line in between the Ubuntu and Windows boot options but it hides the Windows options. These can however be easily found simply by pressing down past the end of the Ubuntu options. Simple but nifty.
[URL="http://stephen.blog.kraya.net/2009/04/09/editing-grub-on-ubuntu-810/"]
Full Instructions on my blog: http://stephen.blog.kraya.net/2009/04/09/editing-grub-on-ubuntu-810/[/URL]

---

### Post by darthmob on 2009-04-10
what about this option:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

the options are still there but not displayed at all. pressing escape brings you to the dialog.

---

