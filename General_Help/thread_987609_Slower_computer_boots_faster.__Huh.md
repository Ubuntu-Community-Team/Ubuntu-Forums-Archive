---
title: "Slower computer boots faster.  Huh?"
date: 2008-11-19
forum: General Help
---

### Post by Crusty Juggler on 2008-11-19
I have a Core 2 Duo 1.73 with 1.5gb RAM running a fresh install of Intrepid 32 bit booting in 25 seconds.  Nice.

On a C2D 2.26 with 4gb RAM and a fresh install of Intrepid 64 bit, boot up takes 45 seconds.  What gives?

---

### Post by kuja on 2008-11-19
Looks like Ryan-laptop is starting more things, for starters. What are the speeds of the laptop hard drives? That could make a difference too (among other things). 

However, the real kicker here seems to be that ryan-laptop is all zombied out for the first fifteen seconds and doesn't do a darned thing. I wonder why that is ...

Oh, and  additionally, be sure to reprofile your readahead.list by appending "profile" to the kernel line (do this from grub) (need only be done once every major upgrade or so)

---

### Post by Crusty Juggler on 2008-11-19
Both laptops have 5400 rpm HDDs.  Though, the 1.73 (sarah) has a 120 GB HDD and the 2.26 (ryan) has 2 x 200 GB.

---

### Post by GmAz on 2008-11-19
well, the 2x200gb is probably in raid configuration.  Also, it could be the 64 bit OS. 

But most likely, its the 2x200gb slowing it down.  If it is in fact in a raid configuration, the raid adapter could be initializing and starting the array.  When I used to have my computer set up in a raid array, it would take about 10-15 seconds longer because of the raid chip checking the array and getting functional.

---

