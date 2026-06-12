---
title: "Weird Gparted problem !"
date: 2008-08-03
forum: General Help
---

### Post by castor_troy on 2008-08-03
I recently installed Gparted on my Hardy. When i start it my whole hard disk shows up as unallocated space. i.e 186.31 GB unallocated. (dev/sda)

This is my only hard disk. Everything runs fine. Np problems whatsoever with any app.

In fact i have a dual boot system. Even Win Vista runs fine and the partitions show up.

I can even access all partitions (even the ntfs ones from within ubuntu itself).

Recently i did some changes with acronis disk director in Vista. Is that the reason for this ?

I want to expand the partition on which ubuntu is installed.
How do i go about this ? :confused:

Everything is fine with my computer just that gparted shows that there is nothing on my HDD. :lolflag:

---

### Post by bodhi.zazen on 2008-08-03
> **castor_troy said:**
> Recently i did some changes with acronis disk director in Vista. Is that the reason for this ?

Most likely that is the source of the problem.

Small bit of advice, usually gparted should be run from a live CD as you can not manage mounted partitions.

---

### Post by castor_troy on 2008-08-03
Yes that may be the source of the problem. 
Even GParted run using live cd doesnt show up any partitions.

What should i do now ?????

I want to expand my ubuntu partition. How can i do it without losing all my data ??????:confused:

---

### Post by zvacet on 2008-08-03
@ **bodhi.zazen**

You are probably right,but I expirienced same problem some time ago.Gparted live Cd didn´t recognize any partition and I didn´t change anything.Few days after everything was O.K. again.I never find out what was the reason.Maybe dirty Cd.I don´t know.Most important thing for me is that everything working again.

---

### Post by castor_troy on 2008-08-04
So you suggest that i wait for a few days and then try again ???

And everything else is just working fine. I'm having no problems whatsoever in running ubuntu or any apps.

---

### Post by zvacet on 2008-08-04
> So you suggest that i wait for a few days and then try again ???

No,I just described my expirience.Better solution is to check is CD dirty and is any dust in Cd drive.

---

### Post by castor_troy on 2008-08-04
no there no dirt in cd ............

and GParted run within ubuntu is also not showing up any partitions.

---

### Post by Sef on 2008-08-04
> Recently i did some changes with acronis disk director in Vista. 

Do they show up in Acronis?

---

### Post by castor_troy on 2008-08-04
Yeah they do show up in Acronis.

But i dont want resize volumes with it, lest i do more damage.

---

### Post by HandleWithCare on 2008-08-04
I'm having the exact same problem. I have a dualboot with windows XP, but I have never used a partitioning progrom whatsoever since I installed ubuntu

---

### Post by castor_troy on 2008-08-05
Now this will seem even weirder.

I undid chages that i made using acronis itself and accidentally deleted my swap using vista's partiton manager and bingo ! gparted back to normal. Except that now i dont have any swap (not that its causing any problems though).

---

### Post by bodhi.zazen on 2008-08-05
Sounds like an issue / incompatibility between gparted and acronis.

IMO gparted is the tool of choice, is there some feature it lacks ?

---

