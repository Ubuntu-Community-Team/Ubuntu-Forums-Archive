---
title: "System hangs when using LaCie FireWire Disk"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by spacewan on 2005-07-08
Hi folks!

I have the following problem:
If I connect my LaCie 60GB Firewire disk (external and hfs) to Ubuntu, all seems to be fine @ 1st.
Hotplug and all works fine, i can browse throught the disk and so on.

But if I start to copy files from the FW-disk to my local disk, the system becomes unstable and hangs (need to press the reset button).

I took a screenshot from my logfile and attached it here.
[http://ubuntuforums.org/attachment.php?attachmentid=1602&stc=1](http://ubuntuforums.org/attachment.php?attachmentid=1602&stc=1)

I would be happy if anybody could help or tell me where the problem is.
Thx

---

### Post by SteveGeorge on 2005-07-13
It's giving some sort of error about the drive not being umounted cleanly so it mounts the drive read-only.  Consequently, I'm guessing that you can read files easily (less them etc) but that you can't write anything.

Looks like you're getting an error message to run the right utility so try that first.

---

