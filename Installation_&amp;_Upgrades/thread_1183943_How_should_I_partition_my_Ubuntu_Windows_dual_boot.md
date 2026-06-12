---
title: "How should I partition my Ubuntu Windows dual boot?"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by lettuceman44 on 2009-06-10
Hi guys. I'm going to dual boot Ubuntu and Windows, but I'm not sure how to partition my drive.

Windows would be for my gaming needs, so it would take up the most space, while Ubuntu I will use for more general things.

I have a 320g hard drive, 298 usable, 2gigs of ram.

How should I partition it?

---

### Post by merlinus on 2009-06-10
At a minimum I would suggest:

10G /
20G /home
1.5G /swap

If need be, you might also create an ntfs partition to share data between both ubuntu and windows.

---

### Post by lettuceman44 on 2009-06-10
So, Ubuntu would only need 10gigs?
Also, 20gig for home file? Isn't home only for user configurations?

Also, ubuntu can read ntsfs now?

---

### Post by merlinus on 2009-06-10
Unless you will be installing lots of linux apps, 10G for / is plenty.

If you will not be usiing /home for multiple users and or data, then you can certainly make it smaller.

Ubuntu has been able to read and write to ntfs for at least the last 5 versions.

---

### Post by lettuceman44 on 2009-06-10
> **merlinus said:**
> Unless you will be installing lots of linux apps, 10G for / is plenty.

If you will not be usiing /home for multiple users and or data, then you can certainly make it smaller.

Ubuntu has been able to read and write to ntfs for at least the last 5 versions.
Jeez, where have I been?:-k
If I'm only going to have one user(me), then how small can I have /home?

---

### Post by merlinus on 2009-06-10
Again, it depends upon how many apps you will be installing.  The configurations, etc. for firefox, for example, are about 90MB, and 113MB for thunderbird. more if you tend to keep old emails.  And there are a fair number of default ones as well.

Since you have a large disk, I would not use less than 8-10G.  Better to overestimate than run out of space down the line.

---

### Post by lettuceman44 on 2009-06-10
So about 20g-30g for Ubuntu in total then?

This is what I am thinking about doing.

Windows: 266.5g
Linux Total: 30.5g
                   - /: 20g 
                - /home: 10g
      - /swap: 1.5g with my 2gigs of ram

---

### Post by merlinus on 2009-06-10
Seems good to me.  You might want to consider the four primary partition limit, however, which will create problems if you decide later on to partition your windows installation.

---

### Post by lettuceman44 on 2009-06-10
> **merlinus said:**
> Seems good to me.  You might want to consider the four primary partition limit, however, which will create problems if you decide later on to partition your windows installation.
I don't think that should be a problem.

Thanks for the help!

---

