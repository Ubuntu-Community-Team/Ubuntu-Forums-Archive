---
title: "Canon PIXMA iP2600 in 9.10: filter?"
date: 2009-11-24
forum: Hardware
---

### Post by MindWanderer on 2009-11-24
Hello, all.  Long-time lurker, first-time poster.

After editing the package dependencies to work in Karmic, I was finally able to install my Canon PIXMA iP2600, but when I try to print from it, I get: "There was a problem printing document 'Test Page' (job 1): 'Stopping job because the scheduler could not execute a filter.'"  The printer icon has a big yellow "!" on it.  When I click "Diagnose," I eventually get "The printer's state message is: 'Filter "/usr/lib/cups/filter/pstocanonij" for printer "Canon-iP2600-series" not owned by root.'"

I used sudo chown to change the owner of that file to root.  Result: the "!" goes away and so does the error message, but it still won't print.  It just sits there doing nothing.

I've seen advice on similar questions to try "sudo /etc/init.d/cups restart" but that gives me:
 * Restarting Common Unix Printing System: cupsd                                
Segmentation fault                                                                         [fail]

---

### Post by gerowen on 2009-12-02
Try re-installing CUPS, then delete the printer and re-add it.  I have a printer shared on an Ubuntu server and for some reason when I took my server down for maintenance, my Ubuntu client machine flipped out and gave me that filter error.  All I did was delete and re-add the shared printer and it took off again.

---

