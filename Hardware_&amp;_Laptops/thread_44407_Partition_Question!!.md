---
title: "Partition Question!?!"
date: 2005-06-26
forum: Hardware &amp; Laptops
---

### Post by orev on 2005-06-26
Working on my second Ubuntu installation.  Would like to get my brother up and running...

Box:  P4 Dell Dimension (Maxtor 80GB HD)

Everything is going great with the installation...until I get to the partition.

When I arrive at the "Partition Overview", I have the following:

#1 Primary    41.1MB    fat16
#2 Primary    20GB       ntfs
   pri/log        60GB    FREE SPACE

The difficulty I am having is that I don't seem to be able to change the size of the free space, or rather, the fat 16 partition.  I was able to change the ntfs partition size, but the remaining went to free space.  (I should be able to eliminate free space all-together, right?)

I need to be able to set up GRUB to dual boot WinXP (he need's IE for a special website for his work, I tried Firefox - no go - would like to get out of WinXP completely.  Maybe someone has a suggestion here...but that's another post... :)  AND here it is:  [http://ubuntuforums.org/showthread.php?p=229146#post229146](http://ubuntuforums.org/showthread.php?p=229146#post229146) )

Can someone point me to a url or advise me on the way to be able to change the partition setup to a 50%(fat16-WinXP) / 45%(ntfs-ubuntu) / 5% (ubuntu swap).

Your kindness will be repaid.

Thank you.

---

### Post by mohaham on 2005-06-26
you have to create two ext3 or reiserfs partitions in the FREESPACE one for / (ubuntu root) and the other for /swap
as far as i know you cannot change the size of FREESPACE directly,
it gets adjusted when u alter/add partitions

---

### Post by az on 2005-06-26
Okay, It is not a one-step-process to shrink or grow several partitions.  If you shrink the first one, that creates a gap between the first and the second.  Also, you cannot move a partition onto itselt - you need to move the data to another area, to free up some space and then move it back to a lower starting point...  

You are just better off to leave everything as it is and tell the partitioner to use the free space as it sees fit (guided partitioning)

That will create your root and swap partition for you.

It will end up being really close to what you want anyway.


"Your kindness will be repaid."

Latinum.

---

### Post by orev on 2005-06-26
Thanks.  I got it figured out by chilling out a bit and letting the great installer and guided partition tool do its thing.  Just trusting the ubuntu installer....

I guess I just sort of got scared of destroying my brother's main work computer (self employed) and, I guess, scared=stupid(?).

Thank you.

---

### Post by Gezzer on 2005-06-26
[QUOTE=orev]Thanks.  I got it figured out by chilling out a bit and letting the great installer and guided partition tool do its thing.  Just trusting the ubuntu installer....

I guess I just sort of got scared of destroying my brother's main work computer (self employed) and, I guess, **scared=stupid(?).**

Thank you.[/QUOTE]

**scared=stupid(?).**

i believe thats called common sense not stupidity ...

---

### Post by az on 2005-06-26
"scared=stupid"

No, that was a great question.  And probably others will benefit from the fact that you asked.

Keep the "stupid" questions coming!

---

