---
title: "Encrypted Hard drive read only"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by kop316 on 2007-08-24
Hello all,

I just bought a new external hard drive, and I was able to get it encrypted and it mounts perfectly on Ubuntu. The only issue is when Ubuntu mounts it, it mounts it so only the root can write to it. I am able to access the hard drive as my ordinary user, but how can I change the settings so I can write to it ordinarily?

---

### Post by kop316 on 2007-08-25
well  I figured it out if any ones else stumbles upon this issue. whether its encrypted or not, if you make an external HD ext3, you have to give it ownership for your user, so you have to type in the command

"sudo chown user:user mount_point"

so in my case (my user name is chris and the mount point is /media/disk)

sudo chown chris:chris /media/disk

---

