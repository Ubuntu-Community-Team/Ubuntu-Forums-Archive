---
title: "Not privilaged to mount volume"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by jabrown65 on 2009-06-01
I am trying to upgrade a couple of laptops from Intrepid the 9.04 amd64 Live CD. When I put in the CD I get an error saying that I do not have privileges to mount the volume. However, my user is a member of root and can sudo. What is the problem?

I have recently had permissions problems with this user after creating an "admin" user, not realizing that one already existed by default which in Intrepid (at least) creates problems by changing the GID of "admin". I followed a procedure to recover from this which involved changing GID of the admin group back to what it was originally, then creating a "newadminuser" which is a member of the original admin group and re-assigning my normal user with sudo access etc. but am wondering if this hasn't resolved everything...

John

---

