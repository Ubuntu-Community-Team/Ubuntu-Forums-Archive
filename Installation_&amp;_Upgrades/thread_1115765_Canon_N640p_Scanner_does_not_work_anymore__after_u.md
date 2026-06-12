---
title: "Canon N640p Scanner does not work anymore  after upgrade to Intrepid"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by mick316 on 2009-04-04
Please Help, this is very frustrating, I have Googled and I have spent a lot of time searching the forum for an answer to this one. 
Everything was working a treat under Hardy, then after I upgraded to Intrepid, Sane no longer sees my scanner.
 When I invoke XSANE, I hear the scanner making some noises and then I get the error "no devices available". I get the same result when I try to launch as Sudo XSANE.
Thanks in advance for your time.

It's an AMD 64 system running Intrepid 64 bIt.

---

### Post by mick316 on 2009-04-08
I found a work around for this - xsane canon_pp:parport0 . This command works after you change the permissions of parport0.
No matter what I else I try, Xsane will not load the conventional way with just the canon_pp driver.
Hope this helps somebody.

---

