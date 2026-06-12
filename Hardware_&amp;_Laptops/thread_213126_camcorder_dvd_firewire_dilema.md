---
title: "camcorder dvd firewire dilema"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by marcw on 2006-07-10
In order for Kino to correctly interface with my DV camcorder via firewire I need to alter some permissions - I add my ID to the "disk" group.  This seems to be because of the /dev/raw1394 being owned by root:disk.  Anyway, after I perform this group change, Kino works flawlessly.

The problem comes about when I want to then burn a DVD; the DVD won't mount.  Only after I change the "disk" group back to original by removing my ID does the DVD mounting work properly.

So the workaround is to change group perms when I want to use Kino and change it back when I want to burn a DVD.  Kind of a pain, yes?

Is there a better solution?  Thanks!

---

