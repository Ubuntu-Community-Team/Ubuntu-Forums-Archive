---
title: "Remove all Updates"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by DocHoliday52090 on 2009-01-19
Some updates to Intrepid have completely ruined my graphics setup, resulting in me having to deal with half-resolution display and non-working sleep/hibernate.

I filed a bug but it seems to have been ignored in the past week, even though I attached all relevant files. I figure if updates caused this, then if I remove all the updates and move back to the initial release versions, then all should be okay. 

How do I tell Ubuntu to move back to the initial Intrepid packages (completely untouched by Ubuntu updates)?

I tried going to Synaptic and setting Distribution option to "Intrepid" instead of 'highest version", but I think that only applies to new packages, not the ones in the system.

---

### Post by Partyboi2 on 2009-01-19
If you know the packages that were upgraded you could open synaptic package manger and search for them and then highlight them and select "package" then "Force Version" and select earlier version. 
If you are not sure what the updates were you can check in Synaptic History (File>History)

---

### Post by DocHoliday52090 on 2009-01-19
I'm more looking for a systemwide command that would force Ubuntu to downgrade *everything* back to initial release Intrepid. 

I tried reverting xorg and the radeon drivers manually but it didn't seem to fix the problem.

---

### Post by cariboo on 2009-01-20
Unfortunately there is no system wide command to revert to the previous versions.

Jim

---

