---
title: "Problem with 9.04 plus ubuntu_studio"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2009-09-12
Bought a new computer with a 300 gb drive and Vista. Not wanting to mess with Vista, I added a 500 gb drive for linux. Then I installed Ubuntu Studio on the 500 gb drive. It works fine.

Then I installed Ubuntu 9.04 also on the 500 gb drive. Seemed like that much space should give them plenty of space each. I let 9.04 install it's self. 

Now Vista is working like Vista. Hopefully that will be fixed at least to some extent when I get the free upgrade to Seven. In any case it is not seeing much use.

Ubuntu Studio Works well but 9.04 appears to have space problems. Can't update 9.04 as I get the following message:


[IMG]http://readoldbooks.com/Error_Msg.png[/IMG]


As I allowed 9.04 to install itself, thinking it knew what it was doing, it may be a partition size problem. I got the following as to space available:


[IMG]http://readoldbooks.com/Screen_list.png[/IMG]


Whatever the problem is, does anyone have an idea how to correct it?

---

### Post by Partyboi2 on 2009-09-12
Hi, looks like the installer only gave you 6.2 gig for your / partition. You can boot a Ubuntu live cd and use gparted (System>Admin>Partition Editor) to increase the size of your current ext / partition.

---

