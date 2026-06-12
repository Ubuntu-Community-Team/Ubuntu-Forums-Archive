---
title: "HPLIP problems"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by minchina on 2007-01-09
I just upgraded to 6.10 and almost everything works great.  The problem that I am trying to deal with now is getting my HP D4160 printer to work again.

It worked fine under 6.06.  On the new install I ran hp-setup and everything detected fine.  The only problem was that it did not print a test page.  I then went to the printer area of the system settings.  It crashed a few times (which was unexpected) but when it did finally load the printer showed up.  
I tried to print a test page though that and it also did not print.  I get a happy message that the page has printed but, alas, it is a lie.  I also tried to print with open office, but the same problem.  I just get an 'error' in the print queue next to all of the failed prints.

The first thing in the queue is something called "tmpIDO_Bq" if that is at all helpful.


What can I do to get this recognized printer to actually print?

Thanks

---

### Post by 11hjpphty76lkjj on 2007-01-12
Can you run 

tail -f /var/log/messages

try and print and post any errors in the /var/log/messages.

A

---

### Post by minchina on 2007-01-16
I ended up switching my printers and now it works.  I have no idea what was wrong with the printer, but I am happy that it is working now.

Thanks for the help.

---

