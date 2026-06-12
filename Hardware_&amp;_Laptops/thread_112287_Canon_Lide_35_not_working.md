---
title: "Canon Lide 35 not working"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by dj1120 on 2006-01-04
Hi all I am a linux newbie taking the plunge. I am dual booting ubuntu 5.10 on a second hard drive (80 gig maxtor IDE drive main drive is wd sata 250 running windows xp pro)  Liking what I see so far.:  Any way ubuntu detected both my printer and scanner a cannon lide 35 as being on parallel ports. I got the printer working but not the scanner. Went to sane home page it says my scanner is supported and I installed the sane packages in synaptic but it still does not work

Has anyone else had this problem?     
     dj1120

---

### Post by dj1120 on 2006-01-19
Update I got this to work by installing 3 new packages using dpkg -i command

the packages:

libgphoto2-2_2.1.6-5.2ubuntu3_i386.deb
libgphoto2-port0_2.1.6-5.2ubuntu3_i386.deb
libsane_1.0.17-1ubuntu3_i386.deb

I can scan now oh joy!!

---

