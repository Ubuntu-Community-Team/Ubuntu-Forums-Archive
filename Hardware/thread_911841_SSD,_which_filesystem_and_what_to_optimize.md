---
title: "SSD, which filesystem and what to optimize?"
date: 2008-09-06
forum: Hardware
---

### Post by Ub1476 on 2008-09-06
Hi, today I'll be getting my Thinkpad X200 with a 64GB SSD. I plan to install Hardy Heron 8.04.1 or Intrepid, latest alpha. I read around a little and found out that EXT3 was alright to use, as long as I removed swap (shall I just remove it with gparted?), and add some "noatime" options to fstab. Is this correct? This was mostly for those netbooks such as the Eee, so I'm a bit worried I might do thinks worse...

Out of curiosity I also wonder how Windows works with SSD. I presume since they come preinstalled with it, the SSD (with Windows) should be able to last for at least 4 years? I guess it's same with Linux? So many rumors that SSDs get killed quickly nowadays.

EDIT: I read a bit more and it seems that the only advantage EXT3 has over EXT2 is journaling.. Now my comp never really crash on Linux, but you never know with a new laptop. Is journaling important for system recovery? 

Also wonder about reiserfs (which I have used before on SATA). Also journaling filesystem, but it's quick.. Does the "quick" part involve more frequent write cycles or something (which hurts SSDs right)?

---

### Post by SimonleBon on 2009-07-08
I don't know if the write cycle issue is true, according to [*this article*](http://www.storagesearch.com/ssdmyths-endurance.html) you don't have to worry about this.

In the OCZ forum there is also a good thread about SSD optimization for linux. [*Guide Linux - Tips, tweaks and alignment*](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)

I'm also looking around to upgrade my Toshiba P300 notebook with an SSD, so right now I'm reading a good article bout SSD's: [*The SSD Anthology: Understanding SSD's*](http://www.anandtech.com/storage/showdoc.aspx?i=3531).

I have limited my choice to two drives: The OCZ Summit 60GB (€ 200,-) or the Intel X25-M 80 GB (€ 250,-).

---

