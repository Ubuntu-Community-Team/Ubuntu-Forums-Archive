---
title: "Compiz just broke"
date: 2008-08-01
forum: General Help
---

### Post by soulxflare on 2008-08-01
This is an interesting problem.  I got home from work, ran the updates that were available, then ran "GL Desktop."  At this point Compiz crashed, and the system slowed to the point of being unusable.  I use CTRL-ALT-BKSP to get back the the GDM window and reboot.  Now whenever I try to enable Compiz, the system starts to crawl.  Not sure what I did, but if anyone has any ideas to get Compiz back up and running, I would be eternally grateful.

---

### Post by fib1807 on 2008-08-01
Compiz wouldn't have broken if u hadn't done something wrong.I'm an absolute noob but what I could tell u is 
use

sudo apt-get remove compiz

and then

re-install compiz frm Add/Remove.

---

### Post by soulxflare on 2008-08-01
Thanks for the reply fib, but I already did that three times.  I ran "sudo apt-get remove --purge compiz* libcompizconfig* -s" to find all the packages for compiz and removed them all with apt-get.  Each time I re-install, and try to re-enable Compiz, it crashes.  I know things just don't break by themselves, but maybe it was an update from today?

---

### Post by fib1807 on 2008-08-01
:lolflag: Alright

---

### Post by gettinoriginal on 2008-08-01
This happened to me today after downloading updates, at the login screen, I selected options, changed my session to xclient (sp), and then logged in, and all is fine.

---

### Post by soulxflare on 2008-08-01
I seem to have gotten it working, more-or-less.  I removed the package "compiz" (all the others were related to compiz-fusion, so I figured that was a deprecated package), and immediately things started to speed up.  I then rebooted and logged in using xclient script as gettinoriginal suggested, and everything seems back to normal now minus the fact that I don't have compiz running on startup.  I am going to add it to the sessions in a few minutes, but am curious to what runtime parameters to use.  I think that --indirect-rendering should be in there since my video card is an ATI Radeon 9200SE, but are there any others that may improve performance?

---

