---
title: "CD Burner Speed Settings"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by Carrot06 on 2006-12-03
I am having a problem with my Lite-On LTR-52327S (internal IDE connection, which was in a USB external IDE case when Ubuntu was installed) CD Burner where the burn speed is always set to 'Maximum Possible'. I have read other posts on this but can't find a solution. I also have a Pioneer DVR-107D DVD Burner which was connected internally using an IDE cable during the original setup of Ubuntu. 
From reading other posts, I have tried setting the write speed in gconf-editor but that only sets the Pioneer drive speed not the Lite-On drive (which stayed at Maximum Possible). I tested the Live CD the other day to see if it was my Burner that may be causing the problem but I was able to select all available speeds after booting the Live CD.
Is there anything I can reinstall that might fix this problem or some setting that I can change so that i can select my write speed for this Lite-On Burner?

---

### Post by PatrickE on 2006-12-05
Hi,

first of all, I have no solution either for this problem, but at least I wanna share my experience here so maybe someone smarter can guess more clues...

I have exactly the same problem as you, also with a Lite-On Drive (LITE-ON LTR-48246S) which was during setup & is still on an internal IDE cable as hdd, in Edgy Eft 6.10 with 2.6.17. To solve it, I also tried gconf-editor, but it didn't work here either. (The only thing I didn't do yet is a check with the live cd, too busy/lazy so far ;-))

On my way through the bash, google and usenet I just found out that there is some bug in Lite-On's firmware which seems to affect speed issues in cdrecord, but was fixed with "version 2.01" of cdrecord (see comment by "Patrick" [not me ;-)] from Feb 12th 2006 on [http://freshmeat.net/projects/cdrecord/](http://freshmeat.net/projects/cdrecord/) ).

Here on Edgy 'cdrecord -scanbus' shows me that I'm running version 2.01.01a03 of a "Cdrecord-Clone" (whatever this means), so maybe this version is still too old for this bugfix as it seems to be quite the oldest (from 2005!) of all 2.01.x versions of cdrecord (see [ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/) ). So maybe our problem is this bug which can't be (isn't) fixed yet due to the conflicts/arguments between the cdrecord developer and the Debian guys? (see [http://cdrecord.berlios.de/old/private/cdrecord.html](http://cdrecord.berlios.de/old/private/cdrecord.html) and [http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html](http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html) )

On the other side, why would it work then on the live cd, but not on an installed version? And before, I had the really old Suse 8.2 on my pc with the same Lite-On drive where it worked perfectly with cdrecord... So again, I have no clue...

But maybe this info can be of some use for someone who is more capable of solving such problems...

Regards,
P.

---

### Post by Carrot06 on 2006-12-13
Just an Update,  I have tried reinstalling Nautilus, Nautilus CD Burner, CDR Tools, and just about anything else related to CD/DVD burning and Nautilus, and nothing has fixed my problem. I am now thinking I might reinstall with Edgy Eft, unless someone can point me to a fix.

---

### Post by yabbadabbadont on 2006-12-13
I'll probably get flamed for this, but you might try the free eval version of nerolinux and see if it works.  If you have a nero license for the windows version, you can use that same license in linux.  I believe that the eval is fully functional too.

---

### Post by PatrickE on 2006-12-16
As it seems, it's no cdrecorder problem... I just installed K3B and burned a cd with this: It worked perfectly well - also with slower speed according to my choice in K3B's burning dialogue.

So my advice would be to install K3B and try it (I just got rid of Brasero...). All the speed settings trouble seems to be some wicked problem in gnome/nautilus or whatever.

Good luck
Patrick

---

### Post by tommcd on 2006-12-17
I guess I've been lucky, but my Lite-On drive has always worked fine in breezy, dapper, and edgy. I can select speeds down to 4.7x. in CD record and gnomebaker.
[http://us.liteonit.com/us/index.php?option=com_content&task=view&id=159&Itemid=67&limit=1&limitstart=1](http://us.liteonit.com/us/index.php?option=com_content&task=view&id=159&Itemid=67&limit=1&limitstart=1)
I will keep the K3B tip in mind if I ever have a problem though. How is K3B for burning .iso files? Gnomebaker has messed up the md5sums for me a couple of times. CD record never fails.

---

### Post by digbysellers on 2007-03-26
It seems to be working in (tried K3b so far) now with the 6.06 update to 2.6.28! 
Can burn an 8X DVD-R video disc @ 4X on Sony DRU710A with latest firmware, BYX(?)- 5...

---

