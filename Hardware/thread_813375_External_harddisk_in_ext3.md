---
title: "External harddisk in ext3"
date: 2008-05-30
forum: Hardware
---

### Post by hammedhaaret on 2008-05-30
hey.

just got this brand new 750gb samsung spinpoint hard disk along with a cabinet to work as backup etc.

decided to format it to ext3... now im not so sure it was a good idea.

first i had to edit the fstab so it didn't mount as root... do i have to do that on every ubuntu machine i plug it into? oh and now i cant unmount it as anything but root... :(

secondly windows machines can't see it and now i found this bug that it should be mounted with relatime ([https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450))

any suggestions as to another filesystem? or is there solutions i missed.

---

### Post by oVIXx on 2008-05-30
Best bet if your using a dual boot system, (M$ & Linux) is to format the external drive using NTFS. That way both O/S' can recognize it with no bugs. If your using a sole linux system, it wont have to be mounted as part of the native file system using NTFS but as a separate drive. I have an external 750GB drive as well, and it just works this way. A big plus is having an enclosure with both a cooler and a power button, especially with 750GB+ drives. Antec MX-1 is one I can suggest.

Cheers

---

### Post by hammedhaaret on 2008-05-30
thanks. think ill just use that then.

why is it a plus with a cooler? faster?

---

