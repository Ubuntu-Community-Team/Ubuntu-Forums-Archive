---
title: "Force Full Format"
date: 2005-11-04
forum: General Help
---

### Post by Bluefire on 2005-11-04
So I switched back to Windows a bit ago because of the problems I was having with World of Warcraft and Hoary Hedgehog.  I'd like to try ubuntu again (I loved it outside of that), but I can't seem to find a fix to my problem.

Basically, I need to figure out how to do a full format on the hard drive I want to run linux around (how to have it skip bad sectors).

When I switched back to Windows, for fun I had it do a quick NTFS format, and I was getting the same exact file corruption errors in Windows then I was with ubuntu.  Reinstalled Windows, forcing a full format, and the problems were gone.

In Breezy Badger, is there anyway to do a full format and not just a quick format?

Thanks!

---

### Post by Kyral on 2005-11-04
Uhh....I think fdisk does a full format. I'm actually not sure. GParted/QtParted surely would I would think

---

### Post by Bluefire on 2005-11-04
Ah, awesome. I'll give it a shot with ubuntu live before installing.

---

### Post by poptones on 2005-11-04
Those bad sectors get remapped by THE DRIVE, not by the software running on the drive. The way you force the drive to remap those bad sectors is by telling the drive to write to them - ie you do a full format, or just "write zeroes to drive" as I suggest.

If you had windows do a full format then the hard drive itself corrected the problem. You can install whatever OS on there and expect the same results.

One thing: if the drive had many bad sectors then it is failing, and this is only a temporary solution because more WILL appear.

---

