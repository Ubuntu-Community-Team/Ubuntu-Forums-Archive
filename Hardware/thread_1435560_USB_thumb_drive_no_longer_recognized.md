---
title: "USB thumb drive no longer recognized"
date: 2010-03-21
forum: Hardware
---

### Post by mvandemar on 2010-03-21
My machine crashed (powered down unexpectedly) recently with an 8GB thumb drive attached to it. When it came back up I was trying to delete a file in one of the folders, but it kept telling me that the filesystem on the device was read only. Googling lead me to the third post on this thread:

[http://ubuntuforums.org/showpost.php?p=6714597&postcount=3](http://ubuntuforums.org/showpost.php?p=6714597&postcount=3)

When I ran fsck -r, I got a bunch of errors that were identified as "There are differences between boot sector and its backup". I chose option #2, Copy backup to original. Not sure if that what caused the issue or if it was something else, but now the device is no longer recognized, period, when I plug it in. Not only does it not auto-mount, but the output from the mount command is identical both with and without the device plugged in.

Is there something else I can try, or do I now have a (very light) thumb drive shaped paperweight?

Thanks. :)

-Michael

---

### Post by mvandemar on 2010-03-21
Ok, just noticed something new... when I plug the device in, /dev/disk/by-id gets 2 new items added to it:

usb-Kingston_DT_101_II_5B8618000B5B-0:0
usb-Kingston_DT_101_II_5B8618000B5B-0:0-part1

So, *something* is getting recognized. Hopefully that helps.

Thanks.

-Michael

PS. actually, the other /dev/disk/by-* folders get entries added to them too, if needed I can post them all.

---

### Post by mvandemar on 2010-03-24
Anyone..?

Thanks.

-Michael

---

