---
title: "Get Ubuntu in the Vista Boot Loader"
date: 2008-10-27
forum: General Help
---

### Post by iampriteshdesai on 2008-10-27
Save me, I am in deep trouble. I have accidently removed Ubuntu from the startup option. I have installed Ubuntu using Wubi alogside Vista. I used the program "EasyBCD" to muck my PC up. Please save me. I want to get back Ubuntu in Start up without reinstalling it.
I have installed Ubuntu in the C: drive. Save me!

---

### Post by francisc1701 on 2008-10-27
Reading EasyBCD's homepage I couldn't help but notice this: > Automated MBR and BCD backups, boot sector restore kits, support for a dozen+ operating systems, detailed configuration of all boot entries, and award-winning guaranteed technical support is what makes EasyBCD stand out - all for free!
So why don't you try to restore one of those backups - surely you created one?

---

### Post by iampriteshdesai on 2008-10-27
I hadn't done any backup before. However thankfully the problem has been solved. I created a new entry for linux in that program. It created a new .mbr file in Vista C:// drive, So I copied the wubi.mbr file in that forder and renamed it to NeoGrub.mbr That did the trick!
Now I can login to Ubuntu.

---

