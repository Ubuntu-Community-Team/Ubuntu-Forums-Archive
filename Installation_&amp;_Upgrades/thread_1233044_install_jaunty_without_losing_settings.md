---
title: "install jaunty without losing settings"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by corkscrew on 2009-08-06
I have hardy heron installed on a laptop with 3 separate partitions well 4 including swap. root, home, data and swap.

If i do a clean install with jaunty is there any way of keeping all my settings for desktop and programs etc?

---

### Post by megamania on 2009-08-06
> **corkscrew said:**
> I have hardy heron installed on a laptop with 3 separate partitions well 4 including swap. root, home, data and swap.

If i do a clean install with jaunty is there any way of keeping all my settings for desktop and programs etc?
Yes, when you reach the partitioning stage,
- leave the partitions unchanged (size, filesystem...)
- set the root partition to be formatted (I think that's automatic)
- uncheck (i.e. disable) formatting for the other partitions
- assign /home and /data to the proper partitions

I've been doing this since 4.10 and have never had a problem - however, be CAREFUL!

---

### Post by sparklingspecks on 2009-08-06
You could also just backup your home directory. (And save a list of applications through Synaptic "Package Download Script Generation".) Or not?

---

### Post by corkscrew on 2009-08-06
sounds good thanks

---

### Post by megamania on 2009-08-06
> **sparklingspecks said:**
> You could also just backup your home directory. 
I'd say you **should** backup, even when not reinstalling...

---

### Post by louieb on 2009-08-06
I have a separate home partition on my laptop (IBM T30). Did a fresh install of Jaunty over Intrepid without formating /home. Due to the changes in Gnome configuration had some problems  when logged on.   To fix renamed folder .gconf and Gnome added it back with its defaults. 

What sometimes happens - new version of a program combined with settings from previous version can sometimes lead to weird results. lol.

---

### Post by Johann-1.0 on 2009-09-07
> **louieb said:**
> I have a separate home partition on my laptop (IBM T30). Did a fresh install of Jaunty over Intrepid without formating /home. Due to the changes in Gnome configuration had some problems  when logged on.   To fix renamed folder .gconf and Gnome added it back with its defaults. 

What sometimes happens - new version of a program combined with settings from previous version can sometimes lead to weird results. lol.

I had the same problems logging on...Can you tell me how did you fix them? I can't understand: "To fix renamed folder .gconf and Gnome...". What is exactly the procedure I should follow?
Thank you

---

