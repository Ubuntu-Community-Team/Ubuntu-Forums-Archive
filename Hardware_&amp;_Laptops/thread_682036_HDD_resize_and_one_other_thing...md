---
title: "HDD resize and one other thing.."
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by athurber on 2008-01-29
Okay, so I installed Ubuntu Studio and everything went great, I have a 200GB HDD and had it partitioned so that 60GB would be used for linux (I had just plain old Ubuntu then).

When I was installing Ubuntu Studio I decided to resize the partition down to only 25GB because I usually just save stuff to my windows xp drive (I'll get there later).

I resized the partition to 25GB and had 40GB left over that is now not being used at all..... My question is... Is there anyway I can add that 40GB to my windows partition without losing any data?



Also, something that hasn't happened to me ever using Ubuntu... I used to be able to see my "hda1" or my windows xp partition on the Ubuntu desktop and when I viewed my drives. Ever since I got Ubuntu Studio and updated my windows partition doesn't show and I really want to be able to view and use the files on my XP partition!!!


Any help will be much appreciated!!!

---

### Post by logos34 on 2008-01-29
Sounds like you'll need to get the Gparted Live CD.  Expand ubuntu root back the way it was, then shrink it from the other (left) side.  This might take a few hours.  (Because it has to copy and move all the files over).  Now expand windows to the right into the freed space.

---

