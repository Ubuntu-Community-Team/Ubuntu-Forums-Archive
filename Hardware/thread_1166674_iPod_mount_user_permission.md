---
title: "iPod mount user permission"
date: 2009-05-22
forum: Hardware
---

### Post by nanotechnology on 2009-05-22
I recently upgraded to Ubuntu 9.04 Netbook Remix from 8.10.  My iPod nano functioned on 8.04 but not on the new version.  When connected, in mounts in /Media, but instead of the owner showing up as my user, it is root.  Permission for oher users is access files only.  It also does not appear on the netbook remix home screen, nor in rhythmbox.  I am assuming this is all related to the same permissions problem, because this does not occur with my flash drive, which mounts correctly.  When trying to change the permission or owner, terminal said permission was denied, even with sudo.  I have tried multiple times, in case the mount was a fluke, but it persists.

---

### Post by rrenomeron on 2009-08-20
*bump* I'm seeing this too, but it's worked in the past.  Is this an oddball hal problem?

---

### Post by rrenomeron on 2009-08-21
So I managed to fix this following a suggestion I found elsewhere in the forums (lost the link): reboot the computer with the iPod plugged in.

It would be great to know *why* that worked.

---

### Post by dopple on 2010-07-13
Confirmed. This also worked for me.

---

