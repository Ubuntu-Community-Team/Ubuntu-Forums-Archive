---
title: "Old fake raid-0 and new motherboard"
date: 2010-08-15
forum: Hardware
---

### Post by khantastic on 2010-08-15
Hey folks.

Last week my old motherboard (Asus M2N-E) did die all of a sudden :( After a small update, system needed to reboot. After reboot I hear the fans start for ca 2 seconds before the system is shut down again. Tried removing everything except from PSU and motherboard, same symptom. Also tried new PSU.

I had configured a fakeraid-0 on my old motherboard some years ago. Don't remember exactly how  it was configured since it has worked quite well with great performance. What I do remember is that I used the installer of 8.04 to install on the raid using Lilo boot loader.

A new motherboard is on the way (Gigabyte GA-P55M-UD4). Although I have backed up the most important stuff on the raid, there are still data I would really like to recover.

Anyone having any experience with fakeraid being moved to new motherboards? Any useful links or helpful guidelines are highly appreciated.

And to all those who want to say "You should use software raid instead", yeah, I agree. Will use it on the new system :)

---

### Post by Fafler on 2010-08-16
*Maybe *it's as simple as making a image with dd, skipping the first n blocks. Google for a tool, that can detect when the filesystem starts.

---

### Post by ronparent on 2010-08-16
The answer to your question is probably indeterminate. Largely because how Ubuntu implements fakeraid has been inconsistent from release to release. The same is true in Windows because nvidia no longer supports drivers for that chipset for Windows 7.

I have transfered a raid0 set from Ubuntu 8.04 on an Asus MB with an nvidia raid chipset to Ubuntu 8.10 on an ePox MB with the same nvidia chipset with no problem. When I recently transfered them to 9.04 on a Gigabyte MB with an AMD raid chipset all the partition tables and therefore data were lost (I planed on repartitioning so the loss was of no real concern to me). It seems highly unlikely (but not necessarily impossible) that the data would survive a change of that magnitude. Ironically, although the data was lost, the raid0 set retained their original nvidia identity in the metadata despite now being on an AMD raid chipset (both in win 7 and Ubuntu)!

---

