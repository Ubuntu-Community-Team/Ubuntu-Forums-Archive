---
title: "Ubuntu 10.04 Xerox Prints but staples Entire Job"
date: 2011-10-26
forum: Hardware
---

### Post by defunkt on 2011-10-26
Im running Ubuntu 10.04 and am having an issue with a Xerox Workcentre 5790.  I swear i ran into this problem eons ago and i think it had something to do with the collation but I've literally tried every combination.

if i print a document that is 3 pages long, i will get page 1 as the first 3 pages, I've fuddled with the collate options in the system-config-printer menu and can get it to collate the document correctly.  

Now when i choose the staple option, if i want 10 copies, it will put one staple through the 10 copies i just printed instead of stapling each copy.

in my head i think this has something to do with being double collated and the printer is stapling the job because of it.

Can anyone else verify my thoughts on this?

---

### Post by defunkt on 2011-10-26
OK, i did confirm that it is a double collate issue, but i also found out that this is specific to an Open Office issue as well.  Gedit works great, without any problems.

On top of that i also noticed that they are both totally different printer screens...

---

### Post by wyliecoyoteuk on 2011-10-26
Basically, the application is collating the job, which means that it produces one large job consisting of all the sets, which the printer cannot separate.
You need to send 1 set and let the printer produce the copies.
Not having a printer with a finisher, can't really help much, but in Libre office, the print dialogue>print options tab has a "produce separate jobs for collated output" tickbox.

---

