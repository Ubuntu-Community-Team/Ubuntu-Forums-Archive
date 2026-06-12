---
title: "Nautilus Shows Wrong Icon for URL Filetype Defined by assoGiate, but Thunar Doesn't"
date: 2009-11-27
forum: Hardware
---

### Post by OzzyFrank on 2009-11-27
Hi. I used this guide [http://ubuntuforums.org/showthread.php?p=3311005#post3311005](http://ubuntuforums.org/showthread.php?p=3311005#post3311005) to register the **.url** filetype with **assoGiate**. However, the Internet Explorer style icon I specified does not show up in **Nautilus** - it is just a generic plain text icon. However, go to **Thunar**, and it displays the IE icon for the same files.

The guide was for Ubuntu 7.10, and shortly afterwards people started complaining the icon hadn't changed (for other issues getting that guide to work in more recent versions: [http://ubuntuforums.org/showthread.php?t=1338702](http://ubuntuforums.org/showthread.php?t=1338702)).

At the end of the thread, someone suggested this command to refresh the icon cache:

**sudo update-mime-database /usr/share/mime/**

... but even after rebooting, still no change. Any ideas who to get this happening in Nautilus? As I said, assogiate and Thunar both recognise the default icon I defined, so I'm stumped as to why Nautilus isn't "playing ball".

---

### Post by mixmastamyk on 2011-01-27
Any update on this?  I'm desperate to change my .pyc file icons to something else.

This question would probably get better response in another category.

---

### Post by OzzyFrank on 2011-01-27
(I don't know what I possibly clicked wrong, but as far as I knew it was going in General; thanks for pointing it out, but I can't see a way to change it)

No luck yet on my side. I did look around some more, but found nothing, just more people complaining of the same thing.

---

