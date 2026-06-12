---
title: "prepare partition portion of install"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by AndyFreak457 on 2009-01-08
I have tried installing Ubuntu and Kubuntu 

i can get the desktop of each to pop up

once i click on the install icon on the desktop, I get to step 4 of each one and it says prepare partition and i cannot do anything, my HD does not show up 

i have tried though the HD and though a CD/DVD to install 

help?

---

### Post by x22 on 2009-01-08
is your HD ok?  reason for that belief?
tried taking it out & reinstalling?

---

### Post by AndyFreak457 on 2009-01-08
> **x22 said:**
> is your HD ok?  reason for that belief?
tried taking it out & reinstalling?

i dont know why my HD would be a problem
ive used my computer with XP for awhile 
is there a way to reformat the whole computer and start with ubuntu maybe?

EDIT:
just plugged in an external to my comp and tried again and it recognized it 
so why isnt my main HD getting recognized?

---

### Post by AndyFreak457 on 2009-01-09
bump

---

### Post by Mark Phelps on 2009-01-09
To get an answer to your question, you would need to boot from the liveCD, open a terminal window, enter "sudo fdisk -lu" (that's a lower-case ell, not a one), and post the results here.

I suspect that your disk is formatted entirely with NTFS partitions -- and the standard Ubuntu installer can't use those.

---

### Post by AndyFreak457 on 2009-01-12
thank you so much for the reply

what do you recommend i do to get things running

---

### Post by kranny on 2009-01-13
Try Deleting all the Volumes Except the Xp Primary partition(If you dont want more than one ntfs partition) using a Xp cd.And then pop your Live cd and make the other desired partitions.

---

