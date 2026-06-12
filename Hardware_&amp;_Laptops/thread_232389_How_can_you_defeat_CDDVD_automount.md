---
title: "How can you defeat CD/DVD automount?"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by mjgumbley on 2006-08-08
Hi, I'm using an external USB DVD rewriter (LG GSA-2164D) and DVD-RAM media, UDF filesystems. I have software which I'm writing that needs to take control of mounting and unmounting these disks, rather than having them automounted. I have the DVD writing tools installed.


This software is effectively a daemon that'll run on a server without a logged in session, usually. Sometimes, I'll be running it in a session.

I want to be able to insert media without having Nautilus (or is it gnome-volume-manager) automatically mounting the media.

What do I need to change to prevent this automounting under /media/dvdrecorder?

There's nothing in my /etc/fstab regarding this.

Thanks,
Matt

---

### Post by bscbrit on 2006-08-08
Matt, does this help?

[http://www.ubuntuforums.org/showthread.php?t=77964](http://www.ubuntuforums.org/showthread.php?t=77964)

---

