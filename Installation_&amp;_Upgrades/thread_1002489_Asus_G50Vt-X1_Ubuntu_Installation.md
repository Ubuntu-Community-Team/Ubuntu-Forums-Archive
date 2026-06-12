---
title: "Asus G50Vt-X1 Ubuntu Installation"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by mertyamak on 2008-12-05
Hi,
I am new to Ubuntu and its community. I work as a lighting & shading TD for CG industry and i wish to install Ubuntu on my Asus G50Vt-X1 laptop. I have opened this thread just to learn if anyone has attempted to install Ubuntu on this particular hardware and suceeded. What worked fine and what didn't work at all. I am very new to the Linux environment so it is a bit scary for me to troubleshoot the possible problems. So maybe i am hoping to find a step by step guide to this installation. I have also searched through the forums and found out some information on G50V series. I am not sure if that information will work for my hardware though. Any help will be very much appreciated.

---

### Post by riblet on 2009-01-22
I just installed Ubuntu 8.10 on this laptop (dual booting with the default Vista64 install) with only one minor adjustment.

In the BIOS, change the default SATA options from "Enchanced" to "Compatible" - this will prevent you from getting SQUASHFS I/O errors during the installation.  Once the installation is done, you can change the setting back to "Enchanced".

Other than that, everything seems to get working very well.  Next step is to get the latest NVidia drivers (v180.22) up and running.

Stay tuned.

---

### Post by troegs on 2009-01-29
I am actually doing this exact operation as I write this. In fact it was some of the difficulties I've experienced in installing ubuntu into the Asus G50vt-X1 that I received not but a few hours ago, (while I was at class). The first issue I've run into is the one mentioned before. getting an VFS error that repeated over and over and over. I've gone into the bios and changed the parts that were mentioned in the earlier post. 

The trouble comes in that the install step comes after the partition step. So now that I'm running through the install again I am partitioning my previous partition. I've had the computer for less than 3 hours and already the disk is getting chopped up into slivers, (at least that's how it feels). I can't designate the old linux partition to be used. The only option I have is to re-partition the partition I just made. Granded I am only losing about 7 gigs and on a 320 gig HD that's not a major deal but I can't help but feeling a little mad that on my BRAND NEW computer I've already screwed something up and to my knowledge I can't correct my mistake. I still have what looks to be about 127.7 gigs to dedicate to linux, (which is more than my previous laptop even had total). 

I'll keep you posted as to how this all works out. Seems like everything should work fine, and I'll basically be left with a partitioned Linux HD. I'm sure I'll find something to put in the tiny one. oh well.

---

### Post by troegs on 2009-01-29
On the topic of the extra HD partitions, does anyone know of a way I can merge the small one and the large one so that I end up back where I started?

---

