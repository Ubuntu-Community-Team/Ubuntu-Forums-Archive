---
title: "external hard"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by kaiwan on 2007-01-07
What has to be done if a external disk is mounted as read only?

I cant change it on properties, even do I am listed as owner ...

Have found something on ubuntu guide, but it is still a beta, and is advised not to be installed  ...

thanks

---

### Post by aysiu on 2007-01-07
Sounds as if it's NTFS. You can try this:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

I would reformat it to FAT32 or Ext3, though.

---

### Post by kaiwan on 2007-01-07
trying that right now ... and if I format it, do I have to do anything else, or it will be automatically write-read ?

---

### Post by aysiu on 2007-01-07
> **kaiwan said:**
> trying that right now ... and if I format it, do I have to do anything else, or it will be automatically write-read ?
Unlike some other distributions (Mepis, for example), Ubuntu's not quite that sophisticated. You would have to mount it after reformatting it:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) (for FAT32)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) (for Ext3)

Note: If you reformat, you will lose any data currently on the external hard drive.

---

