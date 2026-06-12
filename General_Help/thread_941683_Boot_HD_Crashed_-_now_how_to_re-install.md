---
title: "Boot HD Crashed - now how to re-install?"
date: 2008-10-08
forum: General Help
---

### Post by Danial on 2008-10-08
Hi,

First of all Thanks to all who is reading this or responding to this qustion.
second, I hope I am in right category o post this question.

So here it is:

I had a dual boot installed on my system (XP and Ubuntu 7.10) for a while.  Out of two physical HD, a 60G was main boot drive (with both OS installed on it).  Unfortunately, that died a week ago, and now I can not bring up the system even with live CD of Ubuntu (yes it is old one (6.x).  Everything is failing at grub loader or unable to copy few files from CD (tried two different CDs).
Hopefully, by this weekend, I will get my new HD and will  be re-installing both OS.

I may be wrong to make this assumption but I am thinking that BIOS is still pointing to boot drive to Grub loader and failing as there is nothing.  If this is right assumption, how do I overcome the situation - reset BIOS?  Or just simply wait for new Ubuntu install CD and see if that can load properly?

Any help, guidance, time, a smack on my head for not making any boot CD are all welcome and appreciated.

Danial
:confused:

---

### Post by Forbees on 2008-10-08
you might just have to wait . . . . to me it sounds like the hard drive is shot . .

---

### Post by WWSmith36 on 2008-10-08
Since you have two hard drives you post is a little confusing.

What did you do with the hard drive that died (the one with both OS´s installed)?  What was on the other hard drive?  Typically grub is installed only on the MBR of your primary hard drive.  So if that hard drive is ¨dead¨ I don´t think you would have grub loading at all.

Please provide a more exhaustive explaination.

Thank you

---

### Post by Danial on 2008-10-08
Smith,

Sorry about not very specific details. 
Drive with OS's is completely disconnected (no power, no data cable).  When it died, it literally made cluncking noise on startup (as drive arm was dropping on platters).  I had tried to connect to other EIDE connector and changed cable - just to make sure it is not the board or cable - Results are same on either.  BIOS is not seeing the (damaged) hard drive at all.

Back to your question, the other hard drive has only misc. data on it. I don't remember exact wording of error when I was trying to boot (primary drive disconnected) but I will get back to it little later today and get exact error messages.  Also, I will simply disconnect secondary HD before I try to use Ubuntu Live or Installation CD to see if that make any difference.

Once again, thanks for your time to look into this matter.

Danial

---

### Post by Nasaki on 2008-10-08
Lols,

Your hard drive is definitely dead, as you probably know. The best solution would be do first, get a updated CD. That will generally help alot of your problems. If that doesn't work do a CMOS reset (which you will probably need). Also, make sure to replace your dead hard drive or use your "misc" hard drive as a primary.

---

