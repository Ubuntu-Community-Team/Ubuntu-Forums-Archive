---
title: "cupsd chokes when printing photos"
date: 2005-11-28
forum: General Help
---

### Post by snowsquirrel on 2005-11-28
From Digikam, I try to print 4 photos @ 3.5"x5", on a sheet of photo paper, using the printing wizard which comes with kipi-plugins.  Photos are about 1900x1200 res.  Printer is a HP7260 printerr, and I am using the hpijs with cups.  The driver settings are photo on photo paper (whatever res that works out to be).

Printing 2 photos takes about 5~10 minutes before printer kicks in.    The size of /var increases by about 187MB.  A nice quality printed photo sheet is spit out.

When I try to print 4 photos on the same page, gs runs  at 99% CPU for about 8~12 mins, then goes away, and cupsd take up 99% cpu.  cupsd will continue to run at 99% for a long time.  I have never let it run more that 24hours without removing the job.  But the point is, that nothing ever gets sent to the printer.

I can handle slow, but this just plain does not work.  My machine is no speed demon, but is a dual 1GHz, with 512 MB RAM.

I tried gnome-photo-printer.  The printer kicked in after a  about 30 seconds.  But the quality of the prints sucked, and it is not really the kind of software I'd turn my wife loose on.

This is probably a discussion for the KDE list, or the CUPS list, as either KIPI or CUPS are the problem, but I thought I would try here first.  I get sick of signing up for mailing lists and forums.  I like newsgroups.

Thanks,

~S

---

