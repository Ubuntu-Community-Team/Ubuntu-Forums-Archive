---
title: "Scanner installed but not recognised at startup: Epson Perfection 3490"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by The Waco Kidd on 2006-09-17
I have this scanner installed and working. However, it's rarely recognised by Kubuntu. Bizarely, the only guaranteed way I have of getting it working is to boot into Windows (I run a dual boot with XP) first, then restart. Which seems like a horrible waste of time, so I'm reduced to using the scanner only when I absolutely have to and putting things off for days...

Any help appreciated.

---

### Post by zxee on 2006-09-18
I wonder if you have the latest sane backend? [http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=perfection+3490&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=perfection+3490&bus=any&v=&p=)
Also check out the sane website for info on your model. The support for that model is listed as "good" which is not the final "complete" rating.

---

### Post by The Waco Kidd on 2006-09-18
Thanks for the reply.

I'm a little confused trying to find out which version of the backend I have. According to the sane page it should be snapscan 1.4, I checked synaptic and it's not giving me any result for 'snapscan' 'snap scan' or any variant thereof.

Or is this something that's not going to be in the repositories?

---

### Post by zxee on 2006-09-19
Synaptic would only have sane (which you can think of as the collective backend-it has many backends) so checking your version of sane might be a start. 
I couldn't find a guide here for scanners so I appreciate that setting up a scanner isn't easy. The best bet is to follow the set up guides at the sane site. The command 'which snapscan' should tell you where the snapscan driver is located you could then replace the one on your system with the most recent from sane. Also be sure to follow the sane guide(s) for getting your scanner correctly configured.

---

### Post by noynac on 2006-09-19
I had the same exact problem with that scanner. I had to modify the firmware entry in the snapscan.conf file. Do a search of this forum for esfw52.bin for additional information.

---

