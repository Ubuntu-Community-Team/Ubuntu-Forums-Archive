---
title: "Install of updates failed"
date: 2008-10-27
forum: General Help
---

### Post by pwaugh on 2008-10-27
When I attempted to install updates yesterday I get this error:

E: /var/cache/apt/archives/libguicastcv-gl_2.1.0-git20081018akirad2_i386.deb: trying to overwrite `/usr/lib/libguicast.so.1.0.0', which is also in package libguicast-generic
E: /var/cache/apt/archives/libmpeg3cv-gl_2.1.0-git20081018akirad2_i386.deb: trying to overwrite `/usr/lib/libmpeg3hv-1.5.0.so.1.0.0', which is also in package libmpeg3hv-generic
E: /var/cache/apt/archives/libquicktimecv-gl_2.1.0-git20081018akirad2_i386.deb: trying to overwrite `/usr/lib/libquicktimehv-1.6.0.so.1.0.0', which is also in package libquicktimehv-generic

I would post the "details" from the terminal, but this window cannot be copied for a paste.

Now what do I do?

Patrick

---

### Post by exploder on 2008-10-27
Just a guess but it looks like all of the dependencies were not available at the time you tried to update. You might want to give it another try.

---

### Post by IRENKA on 2008-10-28
Ther's a bug at repository.
Look at comments: [http://akiradproject.net/repository](http://akiradproject.net/repository)

---

