---
title: "Bad hard drive?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by tht00 on 2006-03-25
Alright, this is more of a hardware issue and has nothing to do with Linux/Ubuntu, but this seems the most appropriate place to put it.  Mods, move it if it belongs somewhere else.

Anyway:

I bought an IDE 160GB hard drive (Maxtor, I think) shortely after I bought my computer, almost a year ago.

Shortely after I bought it (I was only running Windows at the time, and using it for storage), it would occasionally stop showing up as a mounted drive (it would simply disappear).  A reboot would fix it.  Eventually, it started working normally, and I forgot about the 'problem'.

Now, once I got into Linux, I put it on my 40G hard drive with Windows, but eventually, I decided it ought to have more space, so onto the 160GB hard drive it went, and everything was great for a couple weeks.

Yesterday, I went to reinstall Windows (always the easiest fix when it breaks), but it simply refused to install where it was before (a 5 gig partition), as it saw a nice big 60GB FAT32 partition it already marked as 'C:\'.  So, to get it to install where I wanted it, I had to open up the computer and physically disconnect the hard drive, and it finally cooperated (XP's installer absolutely sucks).

Now, I think that doing that (opening up the computer and messing with it) brought the problem back to life.  Today, I've had Linux hard lock several times, 5-10 minutes into bootup, and for no good reason - and once it acted funky, like everything on the HD was suddenly gone, which has lead me to believe that the problem I mentioned earlier has come back.  Only to confirm this, I've noticed it in Windows, where one of the FAT partitions was there one moment, and gone the next.

Now, I haven't had any data loss from this, simply that the hard drive _stops_ working whenever it darn well feels like it.  Has anyone seen anything like this?  I downloaded a SMART utility to see if the hard drive was failing, and it says that the drive is in Ok shape.

So, any suggestions?  Is the drive simply bad?  Any hope for it?

It very much aggrivates me... especially seeing how 'reinstalling Windows killed Linux', in a round-about way. Not to mention, I'm now stuck on Windows for the moment, which itself is having issues already. :roll:

---

### Post by Greg2 on 2006-03-25
[QUOTE=tht00]
Now, I haven't had any data loss from this, simply that the hard drive _stops_ working whenever it darn well feels like it.  Has anyone seen anything like this?  I downloaded a SMART utility to see if the hard drive was failing, and it says that the drive is in Ok shape.[/QUOTE]
I would suggest going to the HDD manufacturers web site and d/l their diagnostic utility for that specific drive (all the major manufacturers supply them). Then I would test my drive again with the tools they provide using their instructions.

I had an 80GB Maxtor failure last year. The 'day' before it happened my Linux system stopped responding when trying to open a large bzip2 archive... sounds similar?

---

