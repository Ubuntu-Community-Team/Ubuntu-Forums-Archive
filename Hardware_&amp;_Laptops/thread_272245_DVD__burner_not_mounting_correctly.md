---
title: "DVD  burner not mounting correctly"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by linuxgrrl on 2006-10-05
hi,
I have a DVD burner / combo drive that reads CDs ok but will not read or write DVDs.  When I try to create a DVD, I get this error:
[I]Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount[/I]

From reading other posts, my limited understanding is that the same designation (/dev/hdc) serves as both the CD and DVD since they are in fact the same drive, and there are supposed to be links from /dev/cdrom and /dev/dvd pointing to the /dev/hdc.  So I'm not sure what's wrong, but here's my /etc/fstab:

[I]proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /boot           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/mediavg/videolv    /var/video      xfs     rw,noatime  0   0
/dev/mediavg/photoslv   /var/photos     ext3    rw,noatime  0   0
/dev/mediavg/musiclv    /var/music      ext3    rw,noatime  0   0
/dev/hdc        /media/cdrom0   auto    user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/I]

and here are the links on my systemm:
[I]root@mythbox:/home/mary# ls -la /dev/cdr*
lrwxrwxrwx  1 root root 3 2006-08-29 21:40 /dev/cdrom -> hdc
lrwxrwxrwx  1 root root 3 2006-08-29 21:40 /dev/cdrw -> hdc
root@mythbox:/home/mary# ls -la /dev/dvd
lrwxrwxrwx  1 root root 10 2006-08-29 22:01 /dev/dvd -> /dev/cdrom[/I]

Obviously I've screwed up somewhere, can anyone help?
thanks,
Mary

---

### Post by linuxgrrl on 2006-10-17
anyone?

---

### Post by dannyboy79 on 2006-10-17
i can tell you that I have a cd/dvd-writer and I didn't create any links or whatnot! Why don't you try removing the links and see what happens?

---

