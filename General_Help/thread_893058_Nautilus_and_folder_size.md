---
title: "Nautilus and folder size"
date: 2008-08-17
forum: General Help
---

### Post by stoppage on 2008-08-17
Why Nautilus shows folder size by items and not the actual size in bytes or MB's is something i do not understand.
I also wish it would show info when holding the cursor over a file or folder, like size (again SIZE not just number of items) or the ID tag when holding it over a ogg or mp3.
Does anybody know of an alternative app. that might enable above?
They ought to be standard

---

### Post by rainwalker on 2008-08-22
> **stoppage said:**
> They ought to be standard

+1 for that
I've found many other quirks with Nautilus as well :?

---

### Post by chiossif on 2009-05-29
> **stoppage said:**
> why nautilus shows folder size by items and not the actual size in bytes or mb's is something i do not understand.

+1

---

### Post by MattThLinuxNewb on 2009-05-29
> Why Nautilus shows folder size by items and not the actual size in bytes or MB's is something i do not understand.
I'd say this is because calculating the total size of everything in a directory is quite an expensive operation. (Try selecting the properties of your /media directory and see how long it takes)

Doing it for every visible directory would significantly decrease nautilus' overall performance for something that most users don't need very often (compared with having a fast and responsive file-manager.)
Instead they have made it so you have to specifically view the properties of a directory to see its size. That way if you don't use it, you don't pay for it.

It would be good if nautilus provided an option to enable it for those users who wanted it to behave this way (or who have a super fast CPU and storage drive), there isn't one AFAIK.

---

### Post by theozzlives on 2009-05-29
I'm happy knowing my free space, that's all that concerns me.If I want to know how my disk is being used, there's the Disk Usage Analyzer.

---

### Post by grscjo3 on 2012-12-21
> **MattThLinuxNewb said:**
> I'd say this is because calculating the total size of everything in a directory is quite an expensive operation. (Try selecting the properties of your /media directory and see how long it takes)

Doing it for every visible directory would significantly decrease nautilus' overall performance for something that most users don't need very often (compared with having a fast and responsive file-manager.)
Instead they have made it so you have to specifically view the properties of a directory to see its size. That way if you don't use it, you don't pay for it.

It would be good if nautilus provided an option to enable it for those users who wanted it to behave this way (or who have a super fast CPU and storage drive), there isn't one AFAIK.


Just to be clear... that's exactly what OS X does.  All the things that you say are actually completely done and normal and useful in another OS.  It gives you an option on the properties page.  And then it does the expensive process in a separate thread, in the background, and updates the folders' info when it has it, without decreasing performance.  So what if it's computationally expensive, but done in the background?  If it takes a while, so what, and when it's done you get to see how much stuff is in all your folders.  It's not different than running `du -hs *`, except then people don't have to pop open a shell and cd to that dir and run it.  (In general, nautilus is there for people who don't know how or don't want to interact with their filesystem through the shell, right?)  

+ as many 1's as possible.

---

