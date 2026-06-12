---
title: "New install, many updates - bad package"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2009-03-26
Hi All:
I asked already if I need all the updates that are shown on fresh 8.10 install. I was told probably best.

Well:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.16-10ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.16-10ubuntu0.1_i386.deb)
  404 Not Found

So, do I need to update the library "section' files...??? The above seem to have differing names on the archive directory.

---

### Post by linuxisevolution on 2009-03-26
> **pjmlmas said:**
> Hi All:
I asked already if I need all the updates that are shown on fresh 8.10 install. I was told probably best.

Well:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.16-10ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.16-10ubuntu0.1_i386.deb)
  404 Not Found

So, do I need to update the library "section' files...??? The above seem to have differing names on the archive directory.

looks like their servers are down... again...

---

### Post by Partyboi2 on 2009-03-26
> **pjmlmas said:**
> Hi All:
I asked already if I need all the updates that are shown on fresh 8.10 install. I was told probably best.

Well:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.18.2-0ubuntu2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.16-10ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lcms/liblcms1_1.16-10ubuntu0.1_i386.deb)
  404 Not Found

So, do I need to update the library "section' files...??? The above seem to have differing names on the archive directory.
Try changing your download server to another one in Software Sources (System>Admin>Software Sources>1st tab)

---

### Post by pjmlmas on 2009-03-27
> **Partyboi2 said:**
> Try changing your download server to another one in Software Sources (System>Admin>Software Sources>1st tab)

bingo!, thx!

---

